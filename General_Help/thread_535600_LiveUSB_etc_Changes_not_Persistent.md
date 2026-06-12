---
title: "LiveUSB /etc/ Changes not Persistent"
date: 2007-08-26
forum: General Help
---

### Post by greggooch on 2007-08-26
Hello,
I have followed the instructions for utilizing an Ubuntu 6.10 Live CD to make a USB stick bootable with that OS.  I have a problem - it appears that while most every change I make is persistent (including desktop wallpaper, icons, and various preference settings) it appears that /etc/ changes aren't persistent.  For example, my /etc/fstab and my /etc/network/interfaces lose everything after a reboot.  What's strange is that when booted from my hard disk to inspect the files on casper-rw, they appear correct.  It's almost like the USB boot doesn't read those particular files from casper-rw.

Thanks, 
---==Greg Gooch==---

---

### Post by bobby_d on 2008-01-23
Hi there,
Just realised this problem while using 6.06 persistant - same thing, all the changes are persistent except etc/fstab. My guess is that this file (and others) are recreated fresh at each boot, since if you look for 'fstab' in the File System root (which I guess is unpacked casper-rw) then you find: 

fstab.d folder in /rofs/lib/partman
39create_fstab_header, 40fstab_hd_entries, 50fstab_removable_media_entries files in /rofs/lib/partman/finish.d
fstab file in /rofs/etc

My guess is rofs stands for read-only file system, probably as it is some sort of a blueprint from which eventual files on casper-rw are created.. 

Another guess is if you write something in these files directly, then those changes will be persisted - but haven't tried it yet.. 

Cheers

---

### Post by bobby_d on 2008-01-23
Well, I just tried adding a mount line (which I wanted executed at startup, and so tried to enter it in etc/fstab, which didn't persist) to etc/rc.local, and it persisted and worked !! Phuuhh...

---

