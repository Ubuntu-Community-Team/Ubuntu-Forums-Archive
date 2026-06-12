---
title: "Update fdisk?"
date: 2007-11-01
forum: General Help
---

### Post by Old Pink on 2007-11-01
Hi there,

Recently upgraded from a 5.5GB to a 20GB hard drive in an old laptop, and used dd to transfer the entire installation across.

When now booting from the new 20GB hard drive, with the 5.5GB's installation, it still says I have a a 5.5GB hard drive (in sudo fdisk -l and System Monitor) 

How can I make fdisk update, or take another look at my setup? I mean, I didn't manually enter sizes in the first place, so shouldn't have to manually change things, right? Or if that's the case, how can I accurately do that?

Thanks,
Matt

---

### Post by bingoUV on 2007-11-01
Did you dd the partition, or the whole hard disk?

The filesystem metadata , which you copied from 5.5 GB hard disk, still says the partition is 5.5 GB. Can you post the output of fdisk -l ?  The rest of the 20 GB hard disk is empty. 

You can expand the partition from 5.5 to 20 in gparted. You will have to use a live cd though (can use ubuntu live cd as well).

---

### Post by Old Pink on 2007-11-01
Actually, fdisk is now right:> matt@matt-laptop:~$ sudo fdisk -l /dev/hda1

Disk /dev/hda1: 19.4 GB, 19469205504 bytes
16 heads, 63 sectors/track, 37724 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

Disk /dev/hda1 doesn't contain a valid partition table
matt@matt-laptop:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd679d679

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2367    19012896   83  Linux
/dev/hda2            2368        2432      522112+  82  Linux swap / Solarisbut things like System Monitor and Nautilus are very wrong: 
[img]http://img527.imageshack.us/img527/7913/lollu5.png[/img]

---

### Post by Old Pink on 2007-11-01
No no, I used dd to copy the 5.5GB partition to then 18.xxGB partition on the new hard drive, don't worry, I've not made a 5.5GB partition on a huge hard drive.

---

### Post by bingoUV on 2007-11-01
The ext3 metadata needs to be interspersed with empty space. The following is safe, and might fix the partition. Do it from a live cd when /dev/hda1 is unmounted.
```

sudo e2fsck -p /dev/hda1

```

e2fsck fixes the partition only when extremely safe, but if the data is worth your life to you, back it up before doing this.

---

### Post by Old Pink on 2007-11-01
Hold on a second, even when fdisk sees the right size, this is what I should do? To me it seems alot more, GNOME specific.

---

### Post by bingoUV on 2007-11-01
yes, fdisk just set the partition table in your hard drive. So,
from cylinder  0 to x, partition one
from cylinder x+1 to y, partition two 
and so on.

What exactly is there in the area between 0 to x is not a concern of fdisk. You can dd various stuff there, and fdisk will keep saying that /dev/hda1 means cylinder 0 to x.

But dding anything directly to a partition device is most likely to destroy the filesystem metadata. ext3 for example keeps duplicates copies of its superblock in multiple places, interspersed between empty space. This is why even when you screw up initial part of your ext3 partition, you can tell fsck to fix the partition by fetching superblock from alternate location.

When ext3 looks at its own superblock, it thinks that it is only 5.5 GB in size. It is oblivious to the fact that it is housed in about 19 GB mansion. To make it realize, I think e2fsck should do it automatically. It has fixed even worse situations for me.

---

### Post by Old Pink on 2007-11-01
I tried e2fsck in terminal on the Live CD, but it merely reports "clean" 

As does regular fsck. 

Possibly because I fsck'd as soon as I'd done the dd?

---

### Post by Old Pink on 2007-11-01
What is the difference between fsck and e2fsck? I'm going to go try again with -f 

Any more thoughts? :)

---

### Post by bingoUV on 2007-11-01
well, then I am stumped. Best I can suggest is
1. take the files somewhere else
2. Create the big partition
3. Bring back the files

It is painful, but sure to work.

---

### Post by Old Pink on 2007-11-01
Tried that before dd, totally unbootable, and hard to keep permissions and get things working. Tried sudo e2fsck -f p /dev/hda1 (just what you suggested, but -f forced) and nothing funky was reported. 

I'll go back and try now. Open for suggestions from others!

---

### Post by bingoUV on 2007-11-01
If you were ready to go to those lengths, I would suggest you create a partition of exactly the same size as before. Then dd the stuff. Now you can resize the partition using gparted (from livecd of course).

---

### Post by Old Pink on 2007-11-01
> **bingoUV said:**
> If you were ready to go to those lengths, I would suggest you create a partition of exactly the same size as before. Then dd the stuff. Now you can resize the partition using gparted (from livecd of course).

Far too much work. I'd rather sell the 20GB on and live with 6GB.

---

### Post by Old Pink on 2007-11-02
Anyone at all know how to fix this?

---

