---
title: "Pitfalls to avoid, best methods to use to add SSD to older system"
date: 2014-04-13
forum: General Help
---

### Post by freebird54 on 2014-04-13
I have developed a great impatience with my older system, especially now that my newer one includes an SSD.  I don't expect performance as good overall on the older system (see my sig for relative power), but surely an SSD will elevate it to acceptability!

Can it really be as simple as using dd to copy / over to the new drive?  Should the partition be matched as far as possible? Should I instead try to restore backups onto a fresh build and install? I'm sure you get the idea :)

If I don't hear anything horrifying, I'm expecting to try dd first....

Thanks in advance!

---

### Post by J_Me on 2014-04-13
DD is not the thing to use, try clonezilla instead. The problem with DD is that it copies exactly block for block, including the position of the partition on the old disc which will cause failure at boot time.

---

### Post by Double.J on 2014-04-13
Hi there! 

Well you most certainly can use dd.  an example would be 
```
sudo dd if=/old hdd of=/new/hdd conv=sync,noerror bs=1M
```Now here's the pitfall - if your SSD IS SMALLER THAN YOUR HDD (likely) then it will just keep writing until the disk is full - not everything will be cloned and the partition table will nit match. The target disk (your ssd) needs to be the sane size or greater than the origin to ddthe  whole disk. 

You can first shrink the contents of the disk you want to dd to below that of the ssd. Or you can dd bit by bit - the mbr, then partion 1, then partition2 and so on.

to do the mbr you would need
```
sudo dd if=/dev/sdx of=/dev/sdy bs=512 count=1
```this will only copy the first 512bytes (the mbr)

I have found in the past I make the fewest mistakes if i set up the partition on the disk, then dd just the partitions over, boot from the live cd and use [boot repair]("https://help.ubuntu.com/community/Boot-Repair") to resolve grub. 

As J_me says, clonezilla can be easier!

also if you have system slowdown, the disk is just one of the bottlenecks. You may benefit from reinstalling and just dding your /home and any data partitions over.

in terms of backing up for a total reinstall, we had a great thread [yesterday]("http://ubuntuforums.org/showthread.php?t=2216533") about app backup.

best of luck! Whatever you do, please make sure you have backed up everything first! 

Jj

---

### Post by oldfred on 2014-04-13
Often the better way to have installed to an SSD is not like an older install would be on a hard drive. Or a totally new install. Will you also have data on SSD or just / (root) partition?

Will SSD be only Ubuntu or dual booted?
Does BIOS have AHCI setting for drive. I found I had to stop booting XP on another drive (a good thing) as when I changed BIOS to AHCI XP stopped working. To add AHCI capability to XP was a total new install of XP where newer Windows have drivers you can just add. You need AHCI for trim to work correctly.
You also should format with ext4, but turn journal off to reduce writes. But newer SSDs have lives compatible to hard drives so some now suggest leaving journal on.

I was planning a new system as my dual core is from 2006, about 2 years ago I added a SSD which I planned on transferring to new system. But old system worked so well I have had trouble justifying new system to myself much less my wife. :) .

---

