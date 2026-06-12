---
title: "udev calls my script for &quot;add&quot; but not for &quot;remove&quot;"
date: 2007-08-21
forum: General Help
---

### Post by freemant on 2007-08-21
I've followed [http://ubuntuforums.org/showthread.php?t=164902](http://ubuntuforums.org/showthread.php?t=164902) successfully to setup udev to run a script of mine to automount a usb disk. However, the script is not run when the disk is disconnected (unplugged). My udev rules and script are shown below. From the log file I can see that it is called only when ACTION is "add". If I unplug the usb disk, the symlink /dev/onetouch will indeed disappear so udev is itself catching this event. It is just not calling my script. I am running Ubuntu TLS 6.06. Any help? Thanks in advance!

My rule:
[FONT="Courier New"]BUS=="usb", KERNEL=="sd?", SYSFS{product}=="Maxtor OneTouch III", NAME="%k", SYM
LINK="onetouch" RUN+="/usr/local/admin/handle-onetouch.sh"
[/FONT]
My script:
[FONT="Courier New"]#!/bin/sh
echo $ACTION >> /var/log/tmp
if [ "$ACTION"=="add" ]; then
        echo mounting >> /var/log/tmp
        mount /mnt/usbdisk
else
        echo umounting >> /var/log/tmp
        umount /mnt/usbdisk
fi
[/FONT]

---

