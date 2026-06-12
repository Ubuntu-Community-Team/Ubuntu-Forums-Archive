---
title: "setup wireless through terminal"
date: 2007-12-19
forum: General Help
---

### Post by loganm10 on 2007-12-19
Hello, I run a web server and ftp server using ubuntu desktop. I want to use Ubuntu server to save on resources

The problem is my server uses a wireless card for internet, how do I go about setting it up through the terminal instead of using Network Manager?

I need to know how to specify the SSID, encryption (I use 128 bit WEP), and tell it to use DHCP, and to activate on boot

Many thanks

---

### Post by madking on 2007-12-19
Ok here is the stub stuff

sudo ifconfig DEVICE down
sudo dhclient -r DEVICE
sudo ifconfig DEVICE up
sudo iwconfig eth1 essid ESSID_IN_QUOTES
***SEE COMMENT FOR THIS LINE OF CODE
sudo iwconfig DEVICE mode MODE(THERE IS A LIST BELOW)
sudo dhclient DEVICE

***if it is a ASCII key this is the line you want:
sudo iwconfig key s:KEY

if it is hex use this line
sudo iwconfig key KEY

The modes are:
Ad-Hoc
Managed
Master
Secondary
Repeater
Monitor


Heres an example (if i have confused you...:)):

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "SAmpler"
sudo iwconfig eth1 key s:dogey
sudo iwconfig eth1 mode Ad-Hoc
sudo dhclient eth1



hope that helped :)

---

