---
title: "Grub error 15 not booting"
date: 2008-04-12
forum: General Help
---

### Post by CameronCalver on 2008-04-12
Hey guys one day i booted up my computer and it randomly just said loading grup , error 15 ,..... thats it and i dont no what do to i have no way of backing my 60 gb of stuff somewhere and reinstalling so how do i repair my grub  i need this help urgently thanks.

---

### Post by keratos on 2008-04-12
boot from the liveCD and rerun the boot manager

this will reinstall the MBR

---

### Post by keratos on 2008-04-12
Error 15 is given when GRUB was parsing an internal buffer and expecting a number but found something else.

Could be that the MBR is corrupted.

Boot from the liveCD and rerun the boot manager

this will reinstall the MBR

---

### Post by CameronCalver on 2008-04-12
how do i get to re installing of the boot manager without formatting the disc etc

---

### Post by jdm2 on 2008-04-17
I just had the same thing happen to me kinda.  If you want to backup your data, I recommened a live cd of knoppix.  It saved me majorly.  I was able to backup my stuff and do fsck in it.  You might also be able to install grub with it.  I don't know.  Good luck

P.S. All drives are loaded as read only by default.

---

### Post by keratos on 2008-04-18
> **CameronCalver said:**
> how do i get to re installing of the boot manager without formatting the disc etc

read my previous post.

---

### Post by mardemi on 2008-05-02
> **keratos said:**
> read my previous post.

I tried to rerun the boot manager using these instructions

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

BUT when I type find /boot/grub/stage1, I get the same Error 15 that I get when I try to boot.. it says Error 15, file not found.

Is there another way? I have managed to salvage my important files on to a USB drive but this problem keeps me from even doing a fresh install of Ubuntu, let alone booting my existing installation. The hard drive is a 1-year old 320GB Seagate SATA drive, I doubt that its breaking down already.

BTW, I havent installed Windows even though the instructions refer to that, my problems originally began when Hardy complained of an unclean shutdown during boot and went into an fsck session of some sort (after which I would get a missing home folder warning at login and I couldnt log in). Now I cant even get that far.

---

### Post by tech9 on 2008-05-02
try supergrub disk...

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

you may be able to repair your grub

---

### Post by mardemi on 2008-05-02
> **tech9 said:**
> try supergrub disk...

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

you may be able to repair your grub


Uh, Im using the Hardy Live CD, so I cant burn that thing on to a CD.
I also dont have a floppy drive and my PC doesnt support USB booting.

Is there another way to restore GRUB? Im desperately trying to get it reinstalled, but it wont let me, no matter what I do. If I try grub-install, it just gives me

Could not find device for /boot: Not found or not a block device.

Ive tried mounting and unmounting all my partitions, running fsck and e2fsck, I dont even remember everything. Think Im gonna try the Use Entire Disk option in the partition menu in the installation, see if that will let me maybe format the drive or something and do a reinstall..

EDIT: I was able to do a reinstall, first to the entire disk and then I did another one and managed create a new partition table as well. Bloody hell that was horrible. I won't touch Hardy again, that's for sure. Gutsy all the way.

---

### Post by tech9 on 2008-05-05
> **mardemi said:**
> Uh, Im using the Hardy Live CD, so I cant burn that thing on to a CD.
I also dont have a floppy drive and my PC doesnt support USB booting.

Is there another way to restore GRUB? Im desperately trying to get it reinstalled, but it wont let me, no matter what I do. If I try grub-install, it just gives me

Could not find device for /boot: Not found or not a block device.

Ive tried mounting and unmounting all my partitions, running fsck and e2fsck, I dont even remember everything. Think Im gonna try the Use Entire Disk option in the partition menu in the installation, see if that will let me maybe format the drive or something and do a reinstall..

EDIT: I was able to do a reinstall, first to the entire disk and then I did another one and managed create a new partition table as well. Bloody hell that was horrible. I won't touch Hardy again, that's for sure. Gutsy all the way.


I agree gutsy is way more stable

---

### Post by RDL89 on 2008-05-14
I'm having a similar problem, I have gutsy on an external drive, with XP on my internal drive. I had gutsy running fine but I upgraded to Hardy.  Now after two attempts at reinstalling gutsy I cannot boot into it. I use super grub disk to boot Ubuntu, but after reinstalling I keep getting error 15.

---

### Post by Living2007 on 2008-05-15
You would have removed the partiton of Ubuntu and it is trying to trace /grub

you will have to reinstall ubuntu

---

