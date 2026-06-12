---
title: "problem with using tftp"
date: 2008-02-29
forum: General Help
---

### Post by Brando569 on 2008-02-29
this is taken from [my thread over at MSFN ](http://www.msfn.org/board/Killed-Router-t113261.html&pid=742633#entry742633), i figured i would post this question here since posting a linux related question on a microsoft forum isnt that helpful... in a nut shell my linksys wrt54g became bricked after i saved the config i was using i lost internet connectivity and then i tried to clear the NVRAM and that completely killed it, it keeps on saying "connection was reset by server" when i try to save settings or do anything else..

ok so ive successfully de-bricked the router but im having problems sending the firmware over. i cant get a connection going between the router and my computer. i have two interfaces on my computer and im a little confused on how to connect them correctly. im fairly adept at using linux, my installation is kubuntu 7.11, i issued the command /sbin/ifconfig eth0:1 192.168.0.10 netmask 255.255.255.0 and that went as planned.

if i connect one from the pc to the drop box (i live in a university dorm) tftp will send packets, if i make the connection between the router and the pc tftp wont send packets because it says that it cant access the network. if i connect eth0 to the dropbox (from the pc) and eth1 to the router (from the pc) tftp will send the packets but i wont get any acks. if i connect eth0 to the router and then connect the wan port to the dropbox, tftp will send packets but i wont get any acks. ive tried to configure them manually but nothing seems to work. ifup/down keeps saying that it doesnt know what eth0 and eth1 are (Ignoring unknown interface eth0=eth0.), knetworkmanager says eth0 (it says its name is eth0:avahi, same thing for eth1, but yet only loopback is defined in the interfaces file) has my universities IP address but no subnet mask and in kinfocenter eth0 shows a private address (168.254.7.2) and eth1 will pop up sometimes with another private address. im at a loss right now....

*edit*

i just tried it again and all seemed to go well at first. i opened up kinfocenter and saw that i had a working ip again (i could connect to the internet) so i issued /sbin/ifconfig eth0:1 192.168.1.4 netmask 255.255.255.0 and then checked kinfocenter again. eth0 was listed with the working ip address and eth0:1 was listed with 192.168.1.4. so i disconnected from the dropbox and connected to the router and tried to send it..... nothing, connection timed out. i checked kinfocenter and everything was changed, eth0 and eth0:1 were no longer listed instead i had eth0:avahi with an ip of 168.254.7.2 and a subnet of 255.255.0.0 ! now im completely baffled.

if i can get this router working again it would be amazing, if not ill have to buy a new one..

---

