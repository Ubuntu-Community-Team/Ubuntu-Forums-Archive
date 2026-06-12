---
title: "Won't boot. Can I backup packages w/ Live CD?"
date: 2008-07-03
forum: General Help
---

### Post by impel on 2008-07-03
Hello everyone. I really needed to install Windows XP on this system and it completely screwed everything up.

I was already dual booting Ubuntu 8.04 and Windows Vista on one hard drive and was going to add in Windows XP on the secondary drive.

I got to the point in the XP install where it copies files over and then restarts. When it restarted it just said NTLDR is missing. 

I am able to get into Ubuntu using the live CD and have backed up all regular files from both of my systems, but the main effort I put into the system was getting all the extra packages I want.

I read online how you could install a package to backup the packages, but I can't do that on the live CD.

I was wondering if maybe there is a way while on the live CD to setup an active download place so I could download and run the package from one of the harddrives then backup the packages.

Any help would be appreciated, as some of the apps were a pain to install.

Also, would this only backup ones from the package manager? If so, then wouldnt help. Main problem was the ones that happened without that thing.

---

### Post by logos34 on 2008-07-03
Follow [this guide]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub and everything should be fine with ubuntu.

EDIT: check the Bios hard disk boot order first--the XP drive may be first and the bootloader is there.  Switch it back so the vista/ubuntu drive is first.  See if that fixes it

Normally when you install a second windows (same disk or another), it sees the existing windows (here vista) as the 'active' partition and puts the boot files there.  So maybe just a little editing of boot.ini, etc. will fix things on the windows side

try the suggestions here:
[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

---

