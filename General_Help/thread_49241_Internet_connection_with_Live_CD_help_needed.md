---
title: "Internet connection with Live CD help needed"
date: 2005-07-15
forum: General Help
---

### Post by vidal80 on 2005-07-15
Hello.
I am new to Ubuntu, well actually linux all together, and I must say this has been an excellent OS so far. 
I am however having difficulty trying to setup the Live CD for internet connection.

I am connecting my computer to a cable modem so it has a DHCP and not a static IP
The steps I have taken to set this up are as follows:

System -> Adminstation -> Networking
I have 2 ethernet cards within this machine which are both seen by the program as Ethernet Connection Eth0 & Eth1 respectively
Opened the properties of each and placed a check into "This device is configured"
The configuration setting I chose DHCP and clicked on OK
After doing this I activated the connections

I then go to Application -> System Tools -> Network Tools
Under the connection device I select Eth0 as this is the connection with the cable modem attached to it
The configured button is grayed out
The IP address for the device reads Fe80::201:2FF:Fe25:A2D8
Zero (0) packets sent & receive

I decided to power cycle the cable modem and connect it to Eth1 instead and under connecting device chose Eth1
This also produces similar results

The Loopback feature is the only thing showing sent & receive packets so I guess the transport protocol is working correctly

Based on what I describe can anyone tell me what I'm doing wrong here or am I unable to connect to the internet using the Ubuntu Live CD?

One last thing after reading some other forums on getting started 
I used the Sudo PPPOECONF command at the terminal window and it said after scanning the ethernet controllers it's unable to retrieve an IP address as it could not communicate with the host

---

### Post by malacandra on 2005-07-25
I had some trouble too running Live on a laptop.

Try this:

Open a terminal window and type:

sudo dhclient


That should do it. Somethine about Ubuntu leaving out something in the interfaces file.

---

