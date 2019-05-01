# Meross-Node-Red-Comm

This flow is designed around a multi-ip configured host.  It uses one ip gatway to scan (Ping) for a meross device in config mode. When it find a device (response to 10.10.10.1) it sends packets to configure the device in terms of MQTT server, MQTT Port, WiFi SSID, WiFi Password, and the encription 'key' (used for ALL MQTT messages).  The parameters are all set in the'Meross System Parameters' node near the top center.  Credentials must be set for all MQTT nodes (purple).

Known limitations: The flow was written to post messages without checking for acks or errors.  A simple debug monitor is provided to watch the device communications.  The initial version is written to only talk to a single meross device (Togglex without a array of objects).  A future version may address this ('Meross MQTT 'Togglex' Message Template' will have to be re-written as javascrfipt node as object arrays are a problem in mustache)

How does it work...
After configuring the flow variables above and the MQTT creds, put your device into config mode.  Withing 2 minutes it should automatically detect your device and configure it with the supplied data.  The device will re-boot and log into your MQTT server.  At that point the iinput buttons on the left side can be use to generate on, off, dim, and device info commands.  As stated above, output is shown on the debug monitoring node...

MQTT Server setup...
To make the meross devices talk to a MQTT server, it must be configured to do TLS with a CA certificate.  A Mosquitto config file is provided.

Credits...
This flow is largely based on information from https://github.com/albertogeniola (project MerossIot) and https://github.com/bytespider/Meross (Meross).
