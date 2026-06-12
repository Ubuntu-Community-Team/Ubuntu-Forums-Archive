---
title: "Ubuntu don't start after crash"
date: 2008-06-07
forum: General Help
---

### Post by gioloi on 2008-06-07
Hi, first of all, excuse my english
My PC with Ubuntu 8.04 crashed this afternoon, keyboard and mouse didn't respond, so I did a hardware reset. 
After reboot, filesystem check starts, but the procedure stops and a message tells me that I must launch fsck manually. Then the pc enters in shell, and I launch fsck. fsck found several errors and asks me to Clear.. I answer YES all time. When fsck finished, I press CTRL+D to reboot, but the computer don't respond. So I did a hardware reset again... then PANIC. 
The computer doesn't start and several errors appears like :/init: /init <number> - <command (es. modprobe)> not found
then the message:
ALERT! /dev/disk/by-uuid/fd523a1c-15e5-46f6-ae22-047aaa63587d does not exist. Dropping to a shell!
BusyBox v1.1.3 etc..
(initramfs)
I'll do 'ls' and I see that there isn't the 'home' dir...
so I insert my installation CD and first of all I launch the memory test, several errors there too.. and I discover that one of my memory banks are damaged. So I remove the memory bank that causes the errors, but the system still don't start. 
Last, I try to start with live cd, to attempt to save my data, but when I try to mount the following error dialog appears:
<Unable to mount the volume
Details:
mount: wrong fs type, bad option, bad superblock on dev/sda3, missing codepage or helper program, or other error.
In some cases useful info si found in syslog - try dmesg | tail or so>
I'm desperated.. I use computer for work and I need the data in my home..
Please help me.

gioloi

---

### Post by forger on 2008-06-07
how old is it?
boot from the live cd, see if it runs

---

### Post by gioloi on 2008-06-07
As I wrote, I can't mount the drive from live CD. see the previous message for the error

---

### Post by tespio on 2008-06-07
Looks like some hardware broke...
try switching ram or hard drive and retry you'll find what broke

---

### Post by gioloi on 2008-06-07
Yes, it's a Ram failure.. but after removed the damaged memory bank the filesystem is still corrupted.
I found here [http://ubuntuforums.org/showthread.php?t=420285](http://ubuntuforums.org/showthread.php?t=420285)
some directions to try to recover my data.
Now I can acces to the hard drive from the live cd, and I'm trying to recover my home dir to a USB drive..

---

### Post by gioloi on 2008-06-07
After

sudo e2fsck -y /dev/sda3

all is ok, PC is restarted

---

