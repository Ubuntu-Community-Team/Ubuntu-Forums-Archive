---
title: "alternate xubuntu cd install w/wubi"
date: 2007-07-12
forum: General Help
---

### Post by ArtDeco on 2007-07-12
Background:
Trying to install xunbuntu 7 on an older Dell laptop w/only 128mb ram, 10 gig disk as a dual boot win2k / ubuntu system.

I had already tried to install Ubuntu from a live disk and Xubuntu from a downloaded ISO but problems with the old machine stopped me.

So I used wubi - lupin to try to install xbuntu. I will say that this is a very good idea. A program that doesn't require partioning the hard disk is well worth the trouble if it works 

In Between:
Afer rebooting into ubuntu, the Installer seems to hang at configuring language-pack-en-base. Status bar showed 1% for five hours before I gave up and rebooted it into windows.
I think that 128 mb  isn't enough to run the installer although it's enough to run xunbuntu. When I try to boot into linix I get an error message that the install did not complete and then  it reboots me in about 10 seconds.


Now :
I ordered another quarter gig memory stick to bring ram up to 320 mb - can't hurt and RAMs cheap.
The download seems ok - I have a directory called wubi with \boot, \disks,\docs,\install, \logs, \shared, and \tools. Lots of log files and such from where lupin died that I can read with my windows editor which is very cool.

an xubuntu-7.04-alternate-i386.iso in \install and home , swap, and system virtual disks in \disks all exist.

I am searching for the alternate installation manual but can't find anything newer than 4 years ago. Went to where current was supposed to be and got this error:

The requested URL /ubuntu/dists/edgy/main/installer-i386/current/doc/ was not found on this server.

So: AGO if you are reading this :

1 Where is a good alternate install manual ?
2 Is  there any way I can reconfigure the installer or grub from windows to reinstall from where it died or must I download the whole thing all over?

Thanks

---

### Post by ago on 2007-07-12
What exactly do you need to know?

When you uninstall wubi it will offer to backup the ISO and on next run it will run it again. With wubi you have to reinstall from scratch if you interrupt the installation, but there is no need to redownload the ISO. The installation should only take 10-30 minutes.

Otherwise you burn the ISO and boot from it as usual.

---

### Post by ArtDeco on 2007-07-12
Not sure that I know enough to say exactly what I need to know - that's why I'm looking for an install manual. :)

The error I get when I boot ubuntu is:
Can not boot wubi. Please run installation again.
I thought that meant that I could edit the installer's configuration and run wubicd.exe  or some other .exe again.

However, if I understand you correctly,  I need to uninstall the current hosed up installation rather than attempting to fix it. The uninstall will offer to back up the ISO which is only around 700kb. Wubi will then go get everything  else it needs like an install.exe and config files and will run again. Do I get a chance to edit the defaults or pass a parameter from a command line so it doesn't just hang up again ?

Thanks

---

### Post by ago on 2007-07-12
> **ArtDeco said:**
> However, if I understand you correctly,  I need to uninstall the current hosed up installation rather than attempting to fix it.
Correct

> The uninstall will offer to back up the ISO which is only around 700kb.
The ISO is about 700 MB, if it's 700kb you can just delete it.

> Do I get a chance to edit the defaults or pass a parameter from a command line so it doesn't just hang up again ?
Before you reboot you can edit c:/wubi/install/preseed.cfg all paramters are in there but I am not sure you can fix anything. First thing to try is to install only the base system, so replace ubuntu-desktop with ubuntu-base. In this case you only get a shell. Then you need to have network working from console, then you can install all the rest. Retry first with a normal install even though 128MB is on the thin side.

---

### Post by ArtDeco on 2007-07-12
Ok. I will run the uninstall from windows control panel . If the 256 MB of additional Ram shows up by this weekend, I will install the ram first, otherwise I'll try a full install, then just the base as a plan B.

Thanks.

---

### Post by ArtDeco on 2007-07-13
OK. Cool. Did the Uninstall thing, downloaded GParted, and now am waiting on RAM sticks to arrive- weeks pass -I am in Amish country - Gods country because no one else wanted it- and things are REALLY slow here. But Thanks A Lot Ugm6hr. This will work out OK. Also thanks to AGO in the WUBI forum ( if you are reading this (or not)) .Saved me a lot of reading with one line.  You guys are the reason for not just going along with the MS plan for world domination.
_

---

### Post by ArtDeco on 2007-07-14
Installation of Xunbuntu via Wubi on ancient Dell laptop is complete in three easy steps

1)Ran uninstall of Wubi which deleted old files and backed up the good ISO.
2)I put an additional memory stick of 256mb of ram in the Dell 4000 for a total of 320mb.
3)Ran the Wubi install again. I asked me a couple questions, found the ISO, and chugged away for about an hour .

I now have a dual boot Win2K and Xunbuntu laptop without ever partioning the disk. Amazing what a $70 ram stick can do.

Next I'll decide if I can work out the kinks in the Dell - mouse pad, printer, digital camera, and such and just delete Windows - along with the 54 security patches they just sent me.

This thread can be closed.
__________________

---

