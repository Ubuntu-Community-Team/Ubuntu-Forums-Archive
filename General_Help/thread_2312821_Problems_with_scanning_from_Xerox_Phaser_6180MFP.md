---
title: "Problems with scanning from Xerox Phaser 6180MFP"
date: 2016-02-07
forum: General Help
---

### Post by einpekkar on 2016-02-07
Just had to reinstall 14.04 (don't ask why), and of course, all my settings was gone. Adding the network printer was no problem, printing like before. But, scanning? No way Jose. Now, I've been down this road before, but that's a long time ago, and I'm afraid I have lost my way. Any help will be greatly appreciated. Attached are a screenshot of my settings. If you see anything wrong give a holler.

[IMG]https://dl.dropboxusercontent.com/u/87830328/Screenshot%20from%202016-02-07%2019%3A10%3A29.png[/IMG]

---

### Post by sohlinux on 2016-02-07
try to allow port 139 in your firewall

---

### Post by einpekkar on 2016-02-08
The router firewall is disabled, but I tried it anyway. No luck :(

---

### Post by einpekkar on 2016-02-16
Anyone? Any suggestions?

---

### Post by sohlinux on 2016-02-16
can u ping 10.0.0.9? if not check which ip the scanner is using, with ifconfig then use nmap, netstat or arp to make sure its online, if you find its using another ip then add that ip to your config along with the port No.

---

### Post by einpekkar on 2016-03-06
Problem solved. The bloody computer (server) had all by itself, or something, changed IP to 10.0.0.117. Sorry for wasting your time. Should have checked that and not just assumed that everything was like before. OK, I figured that one out myself in the end :redface:

---

