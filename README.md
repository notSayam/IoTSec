# IoTSec

This is part of a project submission for the coursework for the course IoT Security & Privacy at NYU ECE-GY 9393. 

This has two parts. 
The first is the Wi-Fi deauther, this will kick out all devices connected to the selected network. 
The second is an ARP spoofer, this will disable all devices on a network by giving them the wrong mac address thereby dropping all network traffic. 

## Wi-Fi Deauther 
This is the code for the esp32 board. To install it follow the steps below, 

1. Install https://github.com/espressif/esp-idf
2. Make the project with the command "idf.py build" while in the directory of the code
3. Flash the binaries onto the esp32 board while it is connected with the command "make flash"

To use it, plug the esp32 board to power and it should start a wifi hotspot named "Management AP". Connect to it with the password "mgmtadmin".
Next you can open the web interface on IP address 192.168.4.1 by pasting this into your browser. Here you will see the list of all available Access points you can attack. 
Next, select yout access point and click on "attack" after selecting the duration. The esp32 board will now send deauthentication packets to all devices connected to the selected AP. 
This will ensure denial of service to the devices in the network. 

## ARP Spoofer

This is a basic code meant to be hosted on a raspberry pi zero w. First you will need to configure the raspberry pi w with raspberry pi OS or any supported OS. 

1. To do so, flash the OS image on a micro sd card and insert the card into the board. 
2. Copy and paste the code onto the card after boot and initialization. 
3. Install the prerequisites such as scapy. 
4. Run the code on the board
5. configure a firewall rule to drop packets recieved from the device you want block or block all incoming traffic. 

With both of these devices configured you should be able to deactivate any device over a network to ensure your privacy and security. 
