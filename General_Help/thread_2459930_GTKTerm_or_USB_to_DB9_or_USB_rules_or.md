---
title: "GTKTerm or USB to DB9 or USB rules or ???"
date: 2021-03-29
forum: General Help
---

### Post by curbie1 on 2021-03-29
I’m trying to get Ubuntu (18.04) to act as ASCII terminal to connect to an vintage computer I’ve been fixing over the last two years, I finally got it to boot last week with an equally vintage terminal, but the next step is to get my primary Ubuntu system to replace the vintage ASCII terminal.
 
 
 I’m trying to get GTKTerm to work as ASCII terminal through a USB to DB9 converter cable, though a null modem adapter into a DB9 to DB25 converter.
 
 
 I’ve set this USB rule up  
 sudo nano /etc/udev/rules.d/usb2serial.rules
 SUBSYSTEM=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", GROUP="plugdev", MODE="0666"
 
 
 I have the vintage computer running a program which constantly spits out data, but when I connect GTKTerm either direct or with the null modem adapter I get nothing, no data, no garbage, no prompt, nothing.
 
 
 It seems like the rules aren’t correct because no output with or without the null modem adapter, but I’m a Ubuntu user, not a expert.
 
 
 Any ideas?
 
 
 curbie

---

