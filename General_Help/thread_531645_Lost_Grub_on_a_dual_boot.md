---
title: "Lost Grub on a dual boot"
date: 2007-08-21
forum: General Help
---

### Post by Tripletaco on 2007-08-21
I Restored my window XP partition on a dual boot hard drive.  I did this with my restore disc from Toshiba.  After doing this I lost my GRUB boot loader.  My Toshiba Satellite M115-S3094 boots XP just fine now.  Would like to be able to access my Ubuntu partition on the drive too.  How do I get GRUB back?

---

### Post by oilchangeguy on 2007-08-21
> **Tripletaco said:**
> I Restored my window XP partition on a dual boot hard drive.  I did this with my restore disc from Toshiba.  After doing this I lost my GRUB boot loader.  My Toshiba Satellite M115-S3094 boots XP just fine now.  Would like to be able to access my Ubuntu partition on the drive too.  How do I get GRUB back?

if you used the restore cd, ubuntu is no more. the restore cd wipes the drive.

---

### Post by Tripletaco on 2007-08-21
My partition for XP is the size I expected.  I don't think it wiped the whole hard drive.  I think it just wiped the partition I told it to.  Seemed to me there was an option to do it either way.

---

### Post by oilchangeguy on 2007-08-21
> **Tripletaco said:**
> My partition for XP is the size I expected.  I don't think it wiped the whole hard drive.  I think it just wiped the partition I told it to.  Seemed to me there was an option to do it either way.

use the live cd, and see if you can get into the other partition. and confirm ubuntu is still there. grub can be restored via the live cd.

---

### Post by merlinus on 2007-08-21
```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y).

-merlin

---

### Post by ronmarley1 on 2007-08-21
Another option is the Super GRUB Disk.  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Tripletaco on 2007-08-21
How do I get in with the Live CD?  Once I boot up with the Live CD what needs to be done?  I don't want to reformat my Ubuntu if it's still there.

---

### Post by merlinus on 2007-08-21
Open a terminal window and enter the commands one at a time.

Applications/Accessories/Terminal

-merlin

---

### Post by Tripletaco on 2007-08-21
I tried Gparted it didn't do anything for me.  The partitions are still there.  Is the grub boot in a partition of it's own?  

I was looking at Super Grub.  First I'll try the Live CD.  THanks.  Any instruction will help:)

---

### Post by Tripletaco on 2007-08-21
Thanks Merlinus,

You are brilliant!  I had to guess a little if you also meant to substitute the x in "setup (hdx)" with 0.  I was right.  things seemed to work.  

I'd like to make sure I don't have any useless partitions now.  When in Gparted I saw one partition that had a (!) It looked kind of black.  I'm thinking this was some kind of corruption.  I haven't looked at it since we fixed my grub.  Maybe it's good now. Is grub in it's own partition.

This is a long shot, but I was wondering if you knew if the windowsrecovery disk files some companies put on the hard drive are in there own partition and can be removed?  I have my Toshiba recovery disk and don't see why I should waste space on my hard drive.

THanks again for solving my grub problem!!!!

---

### Post by merlinus on 2007-08-21
Whilst running ubuntu, enter this in a terminal window:

```

sudo fdisk -l

```

This will list your partitions.

-merlin

---

### Post by Tripletaco on 2007-08-25
Now I seem to have lost the F8 safe mode function on windows XP :(

---

