---
title: "udev doesn't run xterm"
date: 2006-11-25
forum: General Help
---

### Post by mat.ko on 2006-11-25
I setup udev to run script on USB disc insert. Everything works just fine to the point, when I try invoke new xterm from the script to echo message.

As I see it when start script from udev the xterm or any other xwindow application doesn't start. Script work just fine when running from terminal or double click an run in gnome.

 I'm sure it is lack of my skills. Any suggestion?

UDEV.RULES

KERNEL=="sda1", RUN+="/home/pc/skripty/script.sh" ,OWNER="pc"
# experiment with xterm - unsuccessful 
KERNEL=="sda1", RUN+="/usr/bin/xterm" 


SCRIPT.SH
#!/bin/bash

LOGFILE="/home/pc/log/logusb.log"
sleep 1;
date >> "$LOGFILE"
echo odpojene >> "$LOGFILE"
#echo xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx >> "$LOGFILE"
pumount usbdisk 2> /dev/null
#xterm event
/usr/bin/xterm -bg red -e "echo LABEL && sleep 10"

---

### Post by mat.ko on 2006-11-26
Any wise man around.....

---

