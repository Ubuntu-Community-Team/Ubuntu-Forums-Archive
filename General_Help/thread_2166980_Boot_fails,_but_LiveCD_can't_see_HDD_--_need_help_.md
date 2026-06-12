---
title: "Boot fails, but LiveCD can't see HDD -- need help troubleshooting"
date: 2013-08-11
forum: General Help
---

### Post by cbrace1-gmail on 2013-08-11
I'm having a strange problem that I can't figure out how to solve or even troubleshoot from other posts and lots of web searching. When I startup, the BIOS posts and I get the GRUB selection screen. I select a recovery mode kernel. At some point, I get an error that says that /dev was not found and it falls back into an initrdmfs prompt. I put in the 12.10 LiveCD I have around and reboot. The LiveCD loads, but gives a text message that says something like "general error mounting drives" and then goes about its business loading 12.10. When it gets there, I enter "fdisk -l" from a terminal and get nothing. There is nothing matching "/dev/sd*". If I shutdown and try to boot again without the CD, the BIOS does not find an installation disk. If I then unplug the machine and try again, I start this whole process over.

So, from the fdisk and ls /dev outputs, I get the impression that the drive is not readable. But the fact that I can get into GRUB during some startups makes me think its not quite dead. When I setup the drive /boot, /home and / were all setup as separate partitions.

Either way I think the drive is on the way out (if not already). If possible, I would at least like to just mount it and try to extract the most recent photos/videos that are not backed up. Any suggestions for how I might either figure out if/where the drive can be mounted, or restore the data?

---

### Post by fantab on 2013-08-11
I does sound like the HDD is corrupt.
Boot with any Ubuntu LiveCD and use Gparted to see if it sees the HDD.
Also post the output of:
```
sudo parted -l
sudo fdisk -l
```

To recover/rescue data try [**TestDisk**]("http://www.cgsecurity.org/wiki/TestDisk").

Good Luck...

---

### Post by cbrace1-gmail on 2013-08-13
No, gparted doesn't see the HDD either, only the DVD. It's odd that sometimes it sees the boot partition during startup, but doesn't see it when starting from the DVD...

---

### Post by Slug71 on 2013-08-13
Sounds like you need a new HDD.
Have you check the connection from your HDD to your motherboard? If you tinkered around in there recently, you may have moved the connection loose or something.

---

