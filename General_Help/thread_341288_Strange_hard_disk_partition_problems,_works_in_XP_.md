---
title: "Strange hard disk partition problems, works in XP not in Ubuntu"
date: 2007-01-18
forum: General Help
---

### Post by Tutu 1234 on 2007-01-18
Yesterday my Ubuntu crashed while switching user and I had to hard reset. Since then I have be able to access it, it's on it's own hard disk so after hours of tinkering last night I tried reinstalling, gives me errors during the partitioning stage. So I booted back into windows (1st time since making the swap over) and deleted the partitions and created one taking the whole disk, formatted to NTFS. Tried copy some data onto it, data plays fine, booted back into the livecd loaded fdisk tried to see the partition nothing, tried adding a new partition kept saying the partition has been altered do you want to proceed, I say yes, reload fdisk and it can't see a partition on that drive.

I'm now in windows got it working as an NTFS drive now, going to try filling the drive with data (Overnight as it's a 300gig) and then checking it to make sure the drive isn't kerput. I really want Ubuntu back any other ideas of what can be wrong?

(Am also going to try installing windows xp on it as a single drive in the pc to see if it can boot that.)

---

### Post by zanglang on 2007-01-18
Ok, let me confirm if this is the problem you're having: you've been unable to boot into Ubuntu, so you reformatted the partition to NTFS and tried to reinstall Ubuntu via the Live CD back on it, but it didn't work / couldn't select the ntfs partition to install on?

I believe writing to NTFS is not enabled by default in Ubuntu, which might be causing your install to fail. Why don't you use make the partition FAT32, or if you don't really need Windows to read the partition, EXT3?

Edit: Actually no, wait, I don't think i'm giving the right suggestion. Can you confirm my 1st question first?

---

### Post by Tutu 1234 on 2007-01-18
My patition's have disapeered in linux, can't partition the drive, can't get ubuntu install to do it  either. Partitions in windows and formats, can copy data to it.

---

### Post by cmost on 2007-01-18
You shouldn't ever try to use NTFS partitons for a Linux install.  Remove the NTFS partitions and use ext3.  This can be done with Partition magic or fdisk if you prefer a DOS command.

---

### Post by Tutu 1234 on 2007-01-19
> **cmost said:**
> You shouldn't ever try to use NTFS partitons for a Linux install.  Remove the NTFS partitions and use ext3.  This can be done with Partition magic or fdisk if you prefer a DOS command.

I'm not trying to install Ubuntu to a NTFS drive, I only formatted it to NTFS to see if it works and to see if I could see the file system in device manager (Which shows up the other NTFS fine), seems to work fine in windows but I can't get the livecd to partition it either automatically (Which is what I first had) or using sudo fdisk /dev/hdb and trying to manually partition it.

It's the same iso I used a month ago when I swapped to Ubuntu and I as ready to give windows up forever now I've been in windows 2 days I'm starting to really miss Ubuntu.

The only thing I can think is the hard disk is knackered but until I install windows and see if it can boot that I won't be sure. If windows does work from that hard disk I shall probably back up all my data (I was lucky I had all my important stuff backed up on the windows partition and I've got a 300gig media player that's empty) and try and install Ubuntu on my 120gig. If it does work I shall bite the bullet and get that core duo complete system I've got my eye on, although I shall insist they let me boot the livecd first.

If anyone has a suggestion or a good disk checker I would be very happy because the sooner I get out of windows the better, it's so so slow.

---

### Post by zanglang on 2007-01-20
I think it was the NTFS causing problems. Try getting a Windows partitioning app like PartitionMagic, change the partition to FAT32, and then try rebooting into the Live CD.

---

### Post by Tutu 1234 on 2007-01-20
I'll try that, I do doubt it (When I first put Ubuntu on it was formatted to NTFS with the same partition table as now and Ubuntu installed and partitioned fine. I'm using the same iso, everything should work fine), I would also like to know why my install fudged and I lost all my data. I wasn't using the PC my mum was and all she does is browse the web in firefox, it was logged in fine. I logged out and the screen went black (Except for the mouse pointer), so I typed my password in (Thinking X had crashed) the mouse pointer changed and I could still move it around. Waited 10 minutes still on the same thing so I hit hard reset. When I rebooted the partition table was screwed.

Now I cannot write a linux compatible partition, drive appears to work fine in windows, haven't got a spare drive to put Ubuntu back on.

If I install the drive in a different PC install Ubuntu and move the drive back to the PC how easy is to swap the drivers across and the target pc has a NVidia Gforce in it as does mine will this just work.

---

