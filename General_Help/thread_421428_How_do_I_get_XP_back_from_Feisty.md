---
title: "How do I get XP back from Feisty?"
date: 2007-04-24
forum: General Help
---

### Post by Rob Wesley on 2007-04-24
Greetings.

I has an extra hard disk lying around and thought I'd try out Ubuntu 7, and I really can't get it to work quite right (I'd like to, but I don't have the time right now to get it going).  I installed on this second disk, and I thought, okay, I'll just remove the disk and all will be okay.  The first disk has XPSP2 on it, and now it won't boot.  I tried booting to the CD to get to the recovery console, but the thing just refuses to go to the CD.  I suspect I have to 'repair' the mbr on the main disk, but can't seem to wrap my brain around how to do it.  I can reinstall the disk with ubuntu on it to get to xp, but going through the OS selector every time, when I only need XP (for now) is a pain.  Any hints/suggestions are appreciated.

Thanks

---

### Post by markitect on 2007-04-24
You should be able to boot of your windows cd, open a recover council and simply type fixmbr.  If you cant boot off the windows CD it may have been scratched or something, if other CD's boot.  If you dont mind leaving the other hard drive in there you can simply boot into ubuntu, open up a terminal and:

cd /boot/grub
sudo edit menu.lst  (feel free to use your favorite editor)

change default to match the windows xp entry (numbered from 0)
change the timeout to 0

save changes and reboot


this way grub will automatically just boot up windows

---

### Post by ciscosurfer on 2007-04-24
> **Rob Wesley said:**
> Greetings.

I has an extra hard disk lying around and thought I'd try out Ubuntu 7, and I really can't get it to work quite right (I'd like to, but I don't have the time right now to get it going).  I installed on this second disk, and I thought, okay, I'll just remove the disk and all will be okay.  The first disk has XPSP2 on it, and now it won't boot.  I tried booting to the CD to get to the recovery console, but the thing just refuses to go to the CD.  I suspect I have to 'repair' the mbr on the main disk, but can't seem to wrap my brain around how to do it.  I can reinstall the disk with ubuntu on it to get to xp, but going through the OS selector every time, when I only need XP (for now) is a pain.  Any hints/suggestions are appreciated.

ThanksI'm going to provide two links that will show you how to go either way:
1) [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
2) [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

