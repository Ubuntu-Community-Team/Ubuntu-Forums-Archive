---
title: "samsung usb mounting issues"
date: 2013-08-11
forum: General Help
---

### Post by Drakkenkill on 2013-08-11
Ive been a ubuntu user on and off but his task i have at hand is a new one for me. Ive used lsusb in terminal and this is what i get 

elijah@elijah-s5710f:~$ lsusb
Bus 001 Device 003: ID 07d1:3a09 D-Link System DWA-160 802.11abgn Xtreme N Dual Band Adapter(rev.A2) [Atheros AR9170+AR9104]
Bus 003 Device 008: ID 05c6:1000 Qualcomm, Inc. Mass Storage Device
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The device is the qualcomm msd but im having issues finding the file its in or im really just trying to transfer music to the sd inside the phone....anyone have any ideas?

---

### Post by gordintoronto on 2013-08-11
Is there anything in /media? (command: ls /media) What version of Ubuntu?

I think you are saying that you plug the phone into the USB port and expect its SD card to be mounted, but it's not. This might be fixed by a setting in the phone. Try Googling [phone model] mount ubuntu

---

### Post by 3rdalbum on 2013-08-11
Which version of Ubuntu and is this phone running Android 4 or above?

Due to changes in Android 4.x, you can't mount the phone on Ubuntu 12.10 or earlier, only 13.04 and later.

However you can use the slightly different method of running an FTP server on the phone and connecting to it through wifi. Or upgrade to 13.04 and it will mount normally.

---

