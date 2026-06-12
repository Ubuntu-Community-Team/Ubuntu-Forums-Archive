---
title: "Advice on Partitioning 10 Gigs of HD Space for Ubuntu"
date: 2007-02-12
forum: General Help
---

### Post by acaby on 2007-02-12
I have been testing Ubuntu (6.10) for about 3 days now from the CD. I am now ready to put it on my Hard drive. I have a FAT32. 30 Gig which was almost full (I had 3 Gigs left) I have Been working all day to make room. i.e. Archiving, Transferring to CD's, Etc. and I have about 8 Gigs now. But I am working for at least 10. I know that I cannot go below 10% of capacity for windows.

Question #1

When I get the room and I install from the CD How much do I allocate for the partition?, And how much for my existing Win98SE (Not confident enough yet to start from scratch) Can I do this from the Live CD or do I need to Download and burn another (I think it is the Text version _ I am new to this so I do not really know what the difference is (I assume the text is a more detailed install)
I am confident that if everything works out OK I will want to format and install on a fresh HD. 

Question #2 - When I format and get rid of Windows

The only problem is I have a 7 year old HP 633  P3 with 256 Ram and I have to use the Restore disk to format. What happens to all the drivers for my CD-RW, DVDR,HP psc 750xi Printer and my 2 Wire External DSL Modem. Will Ubuntu pick these up? 
I am sorry if I sound stupid but this is a big step and I am still a little confused.
Thanks in advance for your advice.
Arthur

---

### Post by aysiu on 2007-02-12
If you want enough room to function, 3.5 GB should suffice. If you want a little buffer, 6 GB will give you plenty of room. For weird situations, you may need more than 6 GB.

You can do a barebones Ubuntu installation that's about 1 GB.

---

### Post by wickstopher on 2007-02-12
Question 1:

On my current Ubuntu partition, I am using under 4gb of the allocated space (and I have a fair amount of software installed), so a 10gb partition should do you just fine.  You're also want to create a second ext3 partition for linux swap space...you should be fine with a 1gb swap.  My Windows XP (sorry, not sure about Win9x) partition uses about 6.5 GB of the allocated space, but I don't have much software installed there...basically a few things that I can't do as well in Linux (finale and cubase).  If you're going to do a split partition on your 30gb drive, I would recommend just going half and half.  15gb to the windows partition, 1-2gb for your linux swap partition, and the rest to ubuntu.  The LiveCD includes Gparted and allows you to manually edit your partition table before installing, so it shouldn't be too much of a problem.  I've also done some partition editing with the gparted LiveCD, which you can download from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php"), but the only function there that I wasn't able to do from the Ubuntu LiveCD was growing an existing partition, and it doesn't seem like you'll be needing to do that.

Question 2:
Your drivers from windows will not be "picked up" by Ubuntu.  You should be able to get most hardware working well in Ubuntu, however.  If you're having trouble with anything, search the forums and the wiki, and if you can't find an answer there, you can always post questions to the forum!

When (and if) you do decide to go full-blown with Ubuntu on your system, you can use the aforementioned gparted liveCD to delete your windows partition, and then grow your Ubuntu partition with the freed space.

Hope this helped, and good luck!

---

### Post by acaby on 2007-02-12
> **aysiu said:**
> If you want enough room to function, 3.5 GB should suffice. If you want a little buffer, 6 GB will give you plenty of room. For weird situations, you may need more than 6 GB.

You can do a barebones Ubuntu installation that's about 1 GB.
Thanks

---

### Post by KAL9000 on 2007-02-12
Would it be possible to Have a FAT32 partition andLinux use it as swap. my thinking here is could I use the same 2GB partition for both OS's swap files :P

---

### Post by acaby on 2007-02-12
> **wickstopher said:**
> Question 1:

On my current Ubuntu partition, I am using under 4gb of the allocated space (and I have a fair amount of software installed), so a 10gb partition should do you just fine.  You're also want to create a second ext3 partition for linux swap space...you should be fine with a 1gb swap.  My Windows XP (sorry, not sure about Win9x) partition uses about 6.5 GB of the allocated space, but I don't have much software installed there...basically a few things that I can't do as well in Linux (finale and cubase).  If you're going to do a split partition on your 30gb drive, I would recommend just going half and half.  15gb to the windows partition, 1-2gb for your linux swap partition, and the rest to ubuntu.  The LiveCD includes Gparted and allows you to manually edit your partition table before installing, so it shouldn't be too much of a problem.  I've also done some partition editing with the gparted LiveCD, which you can download from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php"), but the only function there that I wasn't able to do from the Ubuntu LiveCD was growing an existing partition, and it doesn't seem like you'll be needing to do that.

Question 2:
Your drivers from windows will not be "picked up" by Ubuntu.  You should be able to get most hardware working well in Ubuntu, however.  If you're having trouble with anything, search the forums and the wiki, and if you can't find an answer there, you can always post questions to the forum!

When (and if) you do decide to go full-blown with Ubuntu on your system, you can use the aforementioned gparted liveCD to delete your windows partition, and then grow your Ubuntu partition with the freed space.

Hope this helped, and good luck!
Your Response most definately helped. Thank you very much
Arthur

---

### Post by phiphedog on 2007-02-12
KAL9000, no you can't use a fat32 partition for the swap partition.

---

