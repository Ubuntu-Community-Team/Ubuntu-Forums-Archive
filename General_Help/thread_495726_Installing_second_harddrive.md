---
title: "Installing second harddrive??"
date: 2007-07-08
forum: General Help
---

### Post by EmilyRose on 2007-07-08
So, I found an old (maybe new, who knows!!) hard drive in my brothers old room while cleaning it... and I've put it in my computer (tis a sandisk 80gig, I think), and its showing up as Floppy 1 in Computer - and when I try'n open it I get an Unable to Mount the selected Floppy Dive, in details it reads: mount: /dev/ is not a block device - now obviously I know its not a floppy drive, but how do I tell my system that?? Is there anyway to install this w/o re-installing ubuntu? I"m running 6.10 and plan on upgrading to 7.10 whenever it comes out (tried upgrading to fiesty, but it didn't work out and I gave up as I have to use the cd upgrade method... w/ luck by the time 6.10 comes out we'll have broadband over powerlines;)

Anyhow lots of thanks in advance!!

ETA: Also, its entirely possible that said hd is junk, so if theres a way to figure that out, thatd be nice too;)

---

### Post by taurus on 2007-07-08
What's the output of this command from a terminal?

```
sudo fdisk -l
```
Also, make sure the BIOS detects that second harddrive first.

---

### Post by EmilyRose on 2007-07-08
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hda5               1        1916    15390207   83  Linux
/dev/hda6            1917        5121    25744131   83  Linux
/dev/hda7            5122        5306     1485981   82  Linux swap / Solaris
/dev/hda8            5307        9729    35527716   83  Linux

Why would it need to detect it first?? I don't want it to boot from there...

---

### Post by taurus on 2007-07-08
> **EmilyRose said:**
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hda5               1        1916    15390207   83  Linux
/dev/hda6            1917        5121    25744131   83  Linux
/dev/hda7            5122        5306     1485981   82  Linux swap / Solaris
/dev/hda8            5307        9729    35527716   83  Linux

Why would it need to detect it first?? I don't want it to boot from there...

Is /dev/hda your original harddrive?

---

### Post by EmilyRose on 2007-07-08
I dont think so... though it could be, all the linux bits (hda5,6,7,8) are my original hd, while the w95 (hda1) ext im pretty positive is the second... 

Sorry I'm so clueless!!

---

### Post by taurus on 2007-07-08
/dev/hda1 is an extended partition.  Therefore, everything else under it, /dev/hda5-8 are known as logical partitions.  Remember, you can only have four primary partitions so if you want to have more than four, then you need to make one of those primaries into extended partition.  Then, you can create as many logical partitions under that extended partitions.  

Look at your second harddrive to make sure you have set the jumper cable properly.  It needs to be slave since your first harddrive should be a master drive.  If you remove the second harddrive from a machine, then chances are it will be set as a master.  Then, go into the BIOS to make sure the BIOS does detects both drives:  master and slave.

You need to do that first before you can read or access it from Ubuntu.

---

### Post by EmilyRose on 2007-07-08
I'm fairly positive that all my linux partitions are logical... or at least, I thought they were. 

I just checked my bios and the second hd is primary slave while my original hd is primary master. Its wierd because while my comp still boots, it takes like 5+ minutes to do so w/ this second hd in, while before it only took a minute or so...

---

### Post by taurus on 2007-07-08
When you removed that harddrive from another computer, did you reset the jumpers on the back of the drive?  Again, chances are that drive is set as either master or single which you need to reset it as slave since the original drive in your machine should be set at master.

---

### Post by EmilyRose on 2007-07-08
I didn't take it out of another comp, twas just laying in a sleeve... how do I make sure that the jumpers have been reset?

---

### Post by taurus on 2007-07-08
There should be a diagram on the harddrive showing you three settings:  single, master, and slave.  If not, you need to go to manufacture's site and look it up for the model of that harddrive.  

Then, if you look at the backside of the drive, you should see there are three connections:  cable, jumper, and power.  That's where you set your jumpers for your harddrive.

---

### Post by EmilyRose on 2007-07-08
Right, so I reset it so that tis now set as a slave drive, but linux is still identifying it as floppy 1 and not letting me in... thoughts?

Shoud I run gparted and make sure the other partitions i have are logical?? format this hd??

---

