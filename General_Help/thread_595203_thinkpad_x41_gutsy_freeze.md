---
title: "thinkpad x41 gutsy freeze"
date: 2007-10-28
forum: General Help
---

### Post by Sunjammer on 2007-10-28
Hey I have a problem with system freeze.

Facts:
The computer: IBM Thinkpad x41
The OS: Ubuntu 7.10
Compiz-Fusion enabled
--------------------------------------------
The problem:
Every once in a while (to me it appears random) the system freezes.
The mouse will not move and the keyboard will not work. my mp3 keeps playing though ;=)
And if I press the power button or holds it down for 5 seconds or 10 seconds or whatever, nothing  happens. 
The only way to make contact is to disconnect the battery ..
Non of this happens on my other partitions (one with Sabayon and one with WinXP) therefor I don't believe its a hardware issue either ..

I'm kind of blank here ..

Thanks ..

---

### Post by Sunjammer on 2007-10-28
By the way: "Alt-PrtSc REISUB" trick isn't working either ..

---

### Post by Sunjammer on 2007-10-30
same problem on a thinkpad T43p ..

---

### Post by Sunjammer on 2007-10-30
I found this in the systemlog /var/log/messages

Oct 29 09:12:01 ferocitas kernel: [29276.440000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Oct 29 09:12:05 ferocitas exiting on signal 15

I don't know what exactly this means but I managed to identify the pci device as:

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)

This card uses a restricted driver. I have now disabled the thing since I never gonna use it anyhow,,, If things get better and the sudden crashes disappear I will post a status update in this thread ..

------------------------------------------------------

---

### Post by kontraband on 2007-11-06
I have a similar problem with a ThinkPad T43 with ATI graphics. After upgrading from 7.04 to 7.10 the laptop started randomly freezing - sometimes 2 to 3 times a day, sometimes going a day or two with no lock-ups. By lock-ups and freezes I mean systemic loss of control (nothing works anymore) that results in powercycling the laptop. 

I did a clean install (suspecting that maybe somewhere in the upgrade process something got fudged) but to no avail. The freezes persisted. Ubuntu 7.04 works flawlessly, this is strictly a 7.10 problem.

Any thoughts where I may start investigating and  fixing this problem? 

Thank you.

---

### Post by Sunjammer on 2007-11-06
Actually yes,, I got a little further..
The /var/log/messages starts dumping acpi errors, like this:

Oct 31 11:50:43 ferocitas kernel: [40978.500000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.AC__._PSR] (Node ddce3e28), AE_TIME
Oct 31 11:50:43 ferocitas kernel: [40978.500000] ACPI Exception (ac-0095): AE_TIME, Error reading AC Adapter state [20070126]
Oct 31 11:50:44 ferocitas kernel: [40979.000000] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]

And after a good 10 minuttes or so with this crap, the computer hangs.. both x41 and T43p
It's possible to communicate with the crashed laptop over ssh and even remote desktop and samba filesharing..
The real interresting bit is that if u plug in a usb mouse u can actually use it... haha
And by the way,,, during the freeze, xorg uses 98 % system resources...

---

### Post by Sunjammer on 2007-11-06
so if u fire up a terminal and:

tail -f /var/log/messages

u will have a kind of a forecast,, some minutes to save u're work and reboot the system ..
when the acpi errors start u have decent time;=)

---

### Post by kontraband on 2007-11-06
Interesting. 

How do I  fix this?

---

### Post by Sunjammer on 2007-11-06
Actually I'm not sure yet ..

The ibm-acpi package is released under a new name, thinkpad-acpi.
It is possible something happened during some late release, I don't honestly know.
The thinkpad-acpi package is included but not loaded in gutsy so you can:

sudo nano /etc/modules and put in the following line to the bottom of the file: thinkpad-acpi
on next reboot the module is loaded. or you can load it with this command: sudo modprobe thinkpad-acpi

But unfortunatly this want solve the problem. so my next move will be to try to replace thinkpad-acpi with an older version named ibm-acpi. I'm not sure how to do that yet, but I'm gettin' there ;=)

---

