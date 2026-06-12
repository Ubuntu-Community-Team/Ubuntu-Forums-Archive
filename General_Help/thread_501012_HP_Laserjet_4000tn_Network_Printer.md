---
title: "HP Laserjet 4000tn Network Printer"
date: 2007-07-14
forum: General Help
---

### Post by sgilpatr on 2007-07-14
I'm trying to install an HP Laserjet 400tn

I use Admin --> Printing --> new printer

It detects my printer asn an hp lasertet4000

I set DPI to prores1200
paper size to letter
Paper tray:2
Adv tab paper region to letter
Driver: hp laserjet 400 postscript(recomended)
Printer type: Network TCP socket, HP Jetdirect
Connection Host: 192.168.1.103
Connection port 9100

When I print a test page it says Letter test page has been sent to LaserJet-4000.

My printer LCD says "Tray 1 Load Plain A4"

---

### Post by sgilpatr on 2007-07-14
Tried going to localhost:631/printers/

CUPS installed the printer with all the same settings I used, but it filled in the description boxes, When I tried to print a test job I got the same error from the printer

---

### Post by rbmorse on 2007-07-14
If you don't have the HPLIP utility loaded you might try that.

1. delete the existing printer using system administration
2. from a terminal window sudo apt-get install hplip
3  start HPLIP from the menu and select add device, or run sudo hp-setup from a terminal
4. Follow the prompts to setup your printer
5. test when prompted.

---

### Post by sgilpatr on 2007-07-15
Thanks worked great

---

