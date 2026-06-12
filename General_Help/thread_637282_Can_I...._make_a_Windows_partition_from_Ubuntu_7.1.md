---
title: "Can I.... make a Windows partition from Ubuntu 7.10?"
date: 2007-12-10
forum: General Help
---

### Post by tenchu77491 on 2007-12-10
I absolutely love Linux and used my entire hard drive (80 GB) for it. I have used it for a month or two. In the meantime I wanted to play a few games but could not get them to work in Wine, Cedega, or Virtualbox. I dislike VMware. I was thinking the next best thing would be to make a small, 10gb partition for Windows to run on. Is it possible to do it *from* Ubuntu? I would like to make a partition, then restart with the Windows XP CD in, and then select the new partition. Is it possible? If it is possible and I get tired of it, can I erase the partition Windows is on from Ubuntu, freeing the space for me to use?

I am not too techie, so laymen terms would be appreciated. I want to be sure not to mess up my current Ubuntu setup. I just reinstalled Ubuntu and really like my current setup.

---

### Post by Sef on 2007-12-10
Do you have any free space on the disk or is it all used up?

Could you show us how you have it partitioned?

Applications > Accessories > Terminal 

```
sudo fdisk -l
```

Copy and paste it here.

---

### Post by tenchu77491 on 2007-12-10
I have about 50 gigs free. I would like a 10GB partition for Windows.... I hope it's not too hard!

Here is the sudo fdisk -l result:

[B]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9401    75513501   83  Linux
/dev/hda2            9402        9729     2634660    5  Extended
/dev/hda5            9402        9729     2634628+  82  Linux swap / Solaris[/B]

---

### Post by amugofcoffee on 2007-12-10
You could always use GParted: **apt-get install gparted**

---

### Post by logos34 on 2007-12-10
no, you can't use gparted from the root partition...the latter has to be unmounted so you can resize it...Get the gparted live cd (0.3.4) and shrink it from the left, leaving a 10gb space at front of disk.  You can either format as ntfs from gparted or leave the space empty and format it with the Xp install cd.

It'll take quite a while because your root files have to be copied/moved to the right. (windows like to be at the front of the disk, which is why I'd advise doing it that way)

---

### Post by tact on 2007-12-10
It can be done tenchu77491but it is very techy and huge potential to spoil your whole system.

The following is not a guide and is not encouraging you to try this - basically describing the process so you got an idea how scary it is for beginners:
You would need to boot from a CD that has a tool like gparted on it (ubuntu install CD has it).

Then you would need to make space (the 10Gb you want to give to WinXP) by resizing a suitable partition (hda1)

I am not a windows guru... maybe someone else can chip in - does WinXP need to be on the FIRST primary partition?   If so that will force you to make the space in front of where hda1 is now.  This is dangerous!  May involve some major work to get ubuntu to boot again.

If you get so far and can get ubuntu booting and have a spare 10Gb partition - when you install WinXP it will overwrite the MBR so only it will boot - needing you to again boot from ubuntu CD and fix the MBR  and GRUB again.

You will need detailed help on all the above.... are you up for it?  :)

---

### Post by Tristicus on 2007-12-10
GPARTED works good! I have it on a Live CD.

---

### Post by tenchu77491 on 2007-12-10
Seems like a lot of trouble....

---

### Post by logos34 on 2007-12-10
I disagree with tact...it's not dangerous, but yes you will have to [restore grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351") because windows will overwrite the mbr (no way to stop it)...I resize partitions all the time and I don't think it's that big a deal.  You might have to run fsck (file system check) on linux root after resize but it should be ok.

That said, you COULD try to install XP AFTER ubuntu root partition and see if that works...if windows refuses to boot then you'll have to do what I suggested and put it at the front.  It is definitely time consuming to shrink partitions from the left to right.  I just did a windows machine with C: and D:, where the former (system) partition needed more space so I shrank D: from left to right.  Even though it had only ~6 GB it took like three hours (in retrospect I wish I had gone with my initial impulse and just copied the files off, deleted it, made a new smaller one and copied eveything back).  But it's not so simple with system files.

---

### Post by strabes on 2007-12-10
Resizing ntfs partitions is way more dangerous. I've had two windows installs on two separate computers toasted by gparted when shrinking ntfs partitions.

---

