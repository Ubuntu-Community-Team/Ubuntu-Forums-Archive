---
title: "How to format hard drive"
date: 2005-09-15
forum: General Help
---

### Post by Mr.Clark on 2005-09-15
Against my specific instructions, my father has installed Windows for my brother.

He used to have Kubuntu running on a 200Gb hard drive.

Dad persuaded him (I wasn't there) that Leeds Uni wouldn't support or work for it, so he bought a copy of Windows XP Pro.

In my "helpful" mode, I reccommended a 40Gb drive to install the OS onto, and use the 200Gb for storage.

Dad installed it while my brother was at work and now it's reporting both drives to be 40Gb in size (and the second one is unpartitioned with no extra space that Windows can see).

I can't get Windows to see the rest of the disk (even if we boot from the Windows CD, the Setup sees it at 40Gb)

I've got them to boot from the Ubuntu disc and THAT saw it as 200Gb, but when (they say*) they pressed the "Erase everything on disc" option, it installed Ubuntu.

All I want is to get into Windows and format the drive so he has the full capacity.

The BIOS is apparently reporting the size as 33822Mb.

This is wierd, as the Ubuntu picked it up fine as 200Gb

I've got into a terminal window in Kubuntu live, and I just need the Linux commands to either

a) Completely format the drive

or

b) Format it as a 200Gb FAT32 drive (so I can convert to NTFS in Windows)


Any help much appreciated :)

---

### Post by mlomker on 2005-09-15
I've never done that...it's DOS.  lol.

I can tell you that the commands are fdisk and mke2dos.  If you look at the man pages you'll figure it out.  I'd be concerned about the BIOS issue, though.  Windows should certainly be able to see the drive.  Is this a really old motherboard?  In the old days you had to manually run an autodetect.

---

### Post by sethmahoney on 2005-09-15
If its there, cfdisk (I think) provides you with an easier visual interface than fdisk.  It has options to format as fat-something-or-other, too.

---

### Post by Mr.Clark on 2005-09-15
The 200Gb wasn't set on Slave, it was set on Cylinder Limit.

What sort of pointless jumper setting is that??

Anywho. Set it on Slave and it all started working again.

Thanks to everyone for your helpful (and prompt!) responses :grin:

---

