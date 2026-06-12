---
title: "Problem with 2gb SD card"
date: 2008-07-07
forum: General Help
---

### Post by pwyll on 2008-07-07
I have a SanDisk UltraII 2gb SD card I was using in a Sharp Zaurus as the drive for a Debian install.  I had formatted it last year under Xububtu 7.04 with no problems.  I decided to reflash the Zaurus to a newer kernel and decided to reflash the rootfs at the same time.  

In the meantime I have upgraded both my laptop and Ubuntu install so that I am now running Ubuntu 8.04.  Under 8.04 the card had myriad problems--since I was unconcerned with the data I tried to simply reformat. A day later, I have reached the following point:

Ubuntu couldn't handle it.  FSCK would show a clean file system but fdisk, parted and Gparted all showed non-partitioned empty space.  Fdisk could write a filesystem, and see it later, unless I ran Gparted.  Rebooting would render all changes pointless and the entire set of processes would have to be done again.  And to top it all, the most that could ever be recognized by fsck, fdisk, parted or Gparted was 968 meg or "1 GB" depending on where in the process it was checked.

On the other hand, the digital camera and winblows2k both format it to a two gig FAT disk with no problem, w2k either as FAT or FAT32 (though it does not finish an NTSF format).  Installing it under Ubuntu after a winblows or camera format has the filebrowser show it as "2 Gig Media" and after copying 1.89 gig of photos under winblows *all* files were accessible under Ubuntu in the filebowser, but Gparted, parted and fdisk still show it as a 986 meg disk even though all 2 gig is still accessible under the file browser after checking with those programs.

I decided that something must have gone wonky on the card since I'd had no problem formatting it under 7.04 and now couldn't get the formatting tools to see more than a gig even though the filebrowser had no problem, so I resigned the card to my wife's camera and bought a new 2 gig SD card.  I pulled it out of the package and popped it in the card reader.  When the "2 Gig Media" icon popped up, I unmounted the drive and fired up Gparted--and was shown a 986 meg disk ready for formatting.

I have been unable to find any mention of this problem in any Ubuntu or Linux forum and am at a compleat loss as to why 7.04 would be able to handle formatting a 2 gig SD card but 8.04 could not.  I initially thought that perhaps there was some problem with the newer versions of the tools, but I find it nearly impossible to believe that e2fsck, fdisk, parted and Gparted all introduced the same bug at the same time in their development.

Is there some known bug I am missing in my internet searches?  Should I just roll back to 7.04?  Or should I roll even farther back and just go to the mix of Debian and FreeBSD on various machines?


Scott

---

### Post by pwyll on 2008-07-10
I will take it, then, that Hardy simply cannot handle manipulating SD cards over 1 gig in size.  I suppose it would be interesting to see if SDHC cards were also limited to 1 gig, but since I have no gadgets capable of using SDHC it would be a waste of money to buy one simply to satisfy curiosity.

Now I guess it's time to install Debian to the Desktop to see if there's any love there...

---

### Post by danwood76 on 2008-07-10
I have used 2GB SD cards on my ubuntu laptop fine.

When you plug the card in and you see it as 1GB check the system error logs and they might shed some light on the issue.

open up a terminal and run this command:
```

dmesg

```
It will probably say stuff about your card and card reader and possible read errors associated with it.

---

### Post by pwyll on 2008-07-11
If I have formatted it in digital camera or winblows, it is "seen" and accessed as a 2GB card.  Unfortunately, neither of those options will formate the card as ext2/ext3.  I've gone ahead and used one of the cards as 1GB so as to not have the Zaurus sitting useless, but I will format the other as 2GB and compare the dmesg output upon insertion (while it'still" 2GB) and upon running fdisk and/or fsck (the point at which it magically shrinks).

---

### Post by fragos on 2008-07-11
I formated a 16MB SD card to ext2 and did someother tweaking to chage the drive name. My SD card now thinks it's 8MB and I can't get Gparted to see more than 8MB regardless of what I do. I leave my other SD cards formated as FAT so they are compatible with my camera and other devices.

---

### Post by pwyll on 2008-07-11
That would help me think there's just a problem with fdisk/parted and SD cards (or certain SD cards)--except the card in question formatted to 2GB just fine using Gparted under Fiesty 8 or 10 months ago.  That really is my only sticking issue--I'd have no problems accepting a limitation if it hadn't seemed to have been introduced recently  :-/

Thanks for your post--now at least I know I'm not the only one with this (or similar) problem...


Scott

---

