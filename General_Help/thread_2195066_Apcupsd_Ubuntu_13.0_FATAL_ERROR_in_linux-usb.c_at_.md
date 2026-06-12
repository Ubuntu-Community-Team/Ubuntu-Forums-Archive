---
title: "Apcupsd Ubuntu 13.0 FATAL ERROR in linux-usb.c at line 609"
date: 2013-12-22
forum: General Help
---

### Post by Dhuree on 2013-12-22
[FONT=arial]Hi,[/FONT]

[FONT=arial]I need help in setting up apcupsd on Ubuntu 13.04. I hope I am posting in the correct section.
[/FONT][FONT=arial]
I am running apcupsd 3.14.10-2build1 for armhf archirecture ,Ubuntu 13.04 on Beagle Bone Black.[/FONT]
[FONT=arial]
Im getting  "Error contacting apcupsd @ localhost:3551: Connection refused" when I type apcaccess status[/FONT]

[FONT=arial]Below are some details.[/FONT]

[FONT=arial]**ACP UPS Model **: APC BR1500G-IN[/FONT]
[FONT=arial]I am connecting via a cable that has USB in one end and Ethernet plug in other end. USB is connected to computer and ethernet plug is connected to UPS.[/FONT]
[FONT=arial]
[/FONT][FONT=arial]**Output of uname -a**[/FONT]
[FONT=arial]Linux arm 3.8.13-bone32 #1 SMP Fri Dec 13 20:05:25 UTC 2013 armv7l armv7l armv7l GNU/Linux[/FONT]

[FONT=arial]**Output of lsusb**[/FONT]
[FONT=arial]Bus 001 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply[/FONT]
[FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]
[/FONT][FONT=arial]**Output of apctest**[/FONT]
[FONT=arial]2013-12-22 12:39:00 apctest 3.14.10 (13 September 2011) debian
[/FONT]
[FONT=arial]Checking configuration ...[/FONT]
[FONT=arial]Attached to driver: usb[/FONT]
[FONT=arial]sharenet.type = Network & ShareUPS Disabled[/FONT]
[FONT=arial]cable.type = USB Cable[/FONT]
[FONT=arial]mode.type = USB UPS Driver[/FONT]
[FONT=arial]Setting up the port ...[/FONT]
[FONT=arial]apctest FATAL ERROR in linux-usb.c at line 609[/FONT]
[FONT=arial]Cannot find UPS device --[/FONT]
[FONT=arial]For a link to detailed USB trouble shooting information,[/FONT]
[FONT=arial]please see <[http://www.apcupsd.com/support.html](http://www.apcupsd.com/support.html)>.[/FONT]
[FONT=arial]apctest error termination completed[/FONT]
[FONT=arial]
[/FONT][FONT=arial]**Output  of cat /var/log/apcupsd.events**[/FONT]
[FONT=arial]2013-12-22 12:01:45 +0000  apcupsd exiting, signal 15[/FONT]
[FONT=arial]2013-12-22 12:01:50 +0000  apcupsd shutdown succeeded[/FONT]
[FONT=arial]2013-12-22 12:01:50 +0000  2013-12-22 12:02:05 +0000  apcupsd FATAL ERROR in linux-usb.c at line 609[/FONT]
[FONT=arial]Cannot find UPS device --[/FONT]
[FONT=arial]For a link to detailed USB trouble shooting information,[/FONT]
[FONT=arial]please see <[http://www.apcupsd.com/support.html](http://www.apcupsd.com/support.html)>.[/FONT]
[FONT=arial]2013-12-22 12:02:05 +0000  apcupsd error shutdown completed[/FONT]
[FONT=arial]
[/FONT][FONT=arial]I have verified that the same setting have worked in another machine successfully, which rules out issues with the cable or the ups.[/FONT]

[FONT=arial]I'm breaking my head from last night with this :). Any pointers would be very much helpful.[/FONT][FONT=arial]
[/FONT]

---

### Post by Andy_Valencia on 2014-01-21
armhf devices are often configured with less kernel options.  apcupsd apears to require /dev/hiddev* devices,
so check to see if you have that support in your kernel:

gzip -d < /proc/config.gz | grep HIDDEV

If it says something like:

# CONFIG_USB_HIDDEV is not set

then you will need to build a kernel with this option enabled (or get whoever supplied your kernel
to do so).

Hope that helps... Andy

---

