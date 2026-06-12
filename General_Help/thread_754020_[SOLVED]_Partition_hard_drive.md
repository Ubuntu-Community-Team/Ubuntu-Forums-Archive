---
title: "[SOLVED] Partition hard drive"
date: 2008-04-13
forum: General Help
---

### Post by barnowl13 on 2008-04-13
I have read that you can repartition your hard drive without loosing and data by using the live CD?

I ask because I have a hard drive 114.49 GB that is partition G: 19.53 H:94.96 I want to remove the partition so it is just one.

Can this be done?

I at the moment I have 4 drives C: D: G: and H: But when I use Ubuntu it shows  C: D: but sometimes shows G: but another time it will show H: but not both?

So would like to make G: and H: back to just one drive.

So if anyone can give me any pointers on how to do this I would be grateful.

---

### Post by mikewhatever on 2008-04-13
Generally speaking, you can use Gparted live cd to accomplish what you've described. It's the same tool that does partitioning on Ubuntu live CD, but with better gui.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

I don't quite understand your setup, so it's hard to advise further, it would help if you'd posted the output of <sudo fdisk -l>. What is on G and on H? If I understand correctly you'd like to combine the two, right?

---

### Post by barnowl13 on 2008-04-14
> **mikewhatever said:**
> Generally speaking, you can use Gparted live cd to accomplish what you've described. It's the same tool that does partitioning on Ubuntu live CD, but with better gui.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

I don't quite understand your setup, so it's hard to advise further, it would help if you'd posted the output of <sudo fdisk -l>. What is on G and on H? If I understand correctly you'd like to combine the two, right?

Hi thanks for your reply here is the the out put from sudo fdisk -l 

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd178d178

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       14946    99570870    f  W95 Ext'd (LBA)
/dev/hda5            2551       13448    87538153+   7  HPFS/NTFS
/dev/hda6           13449       13514      530113+  82  Linux swap / Solaris
/dev/hda7           13515       14946    11502508+  83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28909b93

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/hdb2            2551       14946    99570870    f  W95 Ext'd (LBA)
/dev/hdb5            2551       14946    99570838+   7  HPFS/NTFS
chris@chris-desktop:~$ 

I have taken off all files off the G: drive and on the H: drive I have most of my music and a few films and photo's.

Yes you are correct I want to remove the partition so I can combine the two.

I have downloaded the two things you have posted and will look at them now. 

Thanks for your help.

---

### Post by mikewhatever on 2008-04-14
Ok, good luck. I hope everything goes well. You might want to start using Linux terminology just to be consistent with the output. See, H:\ and G:\ is Windows terminology, and there is no way for us to know which partitions these are. I'd guess these are hdb1 and hdb5, the two partitions on the second HDD, but there is no way to be sure.

---

### Post by barnowl13 on 2008-04-16
Thanks for your help I will have a go at the weekend in removing the partition. Sorry about still using windows terminology must get out of that habit.
I can now do most things on Ubuntu and I am using it more that windows now and it is just a few little problems like this one that I need to sort out. But so far all is going well.

I may be back if I am unsecessful (:-)) Thanks again for your help.

---

