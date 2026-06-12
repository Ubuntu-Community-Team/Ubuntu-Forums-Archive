---
title: "Cutomize My Ubuntu"
date: 2008-04-11
forum: General Help
---

### Post by GeekModder on 2008-04-11
Ok I guess I will start here I am new to linux, and I like my system to do the things that I need.

I like to check my network, connect to my cisco switch, run test on my network, deploy patches, remote to my servers, remote to my desktops. Basically I want this system to be a network engineering tool. Which also checks my WAN, and gives me a diagram of my network.

---

### Post by tvtech on 2008-04-11
then you don't necessarily want ubuntu.  but you can download all the fun programs that i"m going to suggest and install on ubuntu and created a penetration testing system.   

you want [http://www.knoppix-std.org/]("http://www.knoppix-std.org/")

or check out [http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/]("http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/")

if you lvoe ubuntu and want to get started right away making it a serious pen test system start with downloading [http://www.aircrack-ng.org/doku.php]("http://www.aircrack-ng.org/doku.php")

open a terminal and type 
[COLOR="Red"]username@localhost:~$sudo apt-get install aircrack-ng[/COLOR]  
 this is a wireless network utility invaluable to pen testers and those who want to crack the wep
[COLOR="Red"]username@localhost:~$sudo apt-get install macchanger[/COLOR]
this is a mac changer for those who need to authenticate by mac address but happen to buy a new network card and don't have access to change the switch or router.  
[COLOR="Red"]username@localhost:~$sudo apt-get install wireshark[/COLOR]
this is a general linux port for ethereal  and we all love ethereal!!!

Even the most devout windows service technicians and cisco technicians use linux pen test distros to test the vulnerabilities and strength of the security in their deployed network.  

there are many many more!  if you make a cool enough distro package it and send it around to the rest of the world we all love pen test distros

---

