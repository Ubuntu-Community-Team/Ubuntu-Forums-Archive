---
title: "problems with sd card umount and fsck"
date: 2016-05-12
forum: General Help
---

### Post by JimLS on 2016-05-12
Have Ubuntu 14.04 and an sd card from a Beaglebone Black that was corrupted during a power outage (at least that is my guess).  The BBB won't boot.  I am trying to fix the sd card and am running into issues.  When I connect the sd card I get a window that shows the folders (as expected).  When I try to open a folder (have only tried one or two) I get an error.  After closing this window, in terminal I tried umount to unmount the card and got an error.  I finally got the card unmounted (I think) and tried fsck on it.  It just hangs with no error message.  When I tried to shut down Ubuntu the system doesn't ever complete shutdown - just hangs with the little dots sequentially moving across.

What can I do to prevent auto mounting of this card so I can take an image of the card and try fsck on it?  Any other suggestions?

---

### Post by sudodus on 2016-05-12
Please tell us more about the card: What is the partition table and file systems. You can post the output of the following commands, when the card is connected (and maybe mounted),

```
df

sudo parted -ls

sudo lsblk -fm
```

In order to repair the SD card, you should

1. Boot from another device.

2. Check that the card is unmounted and if not, unmount it with superuser privileges

```
sudo umount /dev/sdx
```

where x is the drive letter (maybe b, c ...).

3. Run fsck for the file system(s) that you want the repair.

-o-

If you cannot unmount the card, it is a bad damage or you are using the wrong method.

If still no luck, you can consider cloning it to another drive with ddrescue and do the repair on the cloned copy. (If there is no unique files there, you can wipe the first megabyte and create a new partition table.)

See this link: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by JimLS on 2016-05-12
Well, that didn't go very well...

All three commands hang the system.  When I connect the sd card (through a USB adapter) a window pops up showing the folders. I was able to right click on the drive name to the left on the window  that opened and get a pie chart of used space on the disk.   But if I click a folder the system hangs.  When I try to shut down the system goes to the screen with the several (5?) dots that light going to the right.  That's as far as it gets.  Last time I forced it off by holding the power switch.  This time I tried pulling the USB to the SD card - it shut down once I pulled the USB.

---

### Post by sudodus on 2016-05-13
It seems that either the SD card or the card reader or the USB port is bad. I agree with you, it is probably the SD card.

Is it important to save data from it? In that case try to clone it to another drive with ddrescue and do the repair on the cloned copy according to the end of my previous post (post #2).

Otherwise I suggest that you try to overwrite the partition table and file system(s) with mkusb. See this link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by Bucky Ball on 2016-05-13
> When I try to open a folder (have only tried one or two) I get an error.

Knowing what error would help us a lot when trying to help you! We are still not sure what the problem is and that will give clues. 

This could simply be an exfat issue. Was the error message something to do with that? Have you exfat-fuse and exfat-utils installed? That might not fix, but it might. Try installing them and find out. If not, easy enough to remove again.

What format was required by the BBB? That may also give some ideas of what could be happening. Have you tried inserting this in another box, another OS? Windows? Mac? Same issue? Give more clues with error messages there?

---

### Post by JimLS on 2016-05-13
Trying to open a folder under ubuntu doesn't give an error message.  It just hangs similar to the command line commands.  The card reader is ok - I have tried it with other sd cards and it works.  Windows tells me there is a problem that is probably due to improperly closing files due to improper shutdown or power loss which is exactly what happened.  It offers to try to scan and fix or skip scanning.  I skipped since I wasn't sure that it would fix it properly.  It showed me some documents and files that looked ok.  I think this disk has two partitions - one that windows can understand and one that is the linux OS (and probably swap) - I will check out a similar, good image to see what is should have.

If it isn't a terrible amount of work I would like to repair it since I have a fair amount of time in configuration of various programs.  If not I will start over.  Nothing I can't recreate with a bit of work.  I will try the ddrescue route.

---

### Post by sudodus on 2016-05-13
Good luck with ddrescue :-)

---

### Post by Bucky Ball on 2016-05-13
Put it back in Windows and let Windows fix it. The shutdown error issue is pretty straightforward.

I'm no longer au fait with Windows, but I don't think the shutdown fix erases the partitions. You might want to check that first if there is anything you don't need to save. If not, go for it.

---

### Post by JimLS on 2016-05-13
I did the windows fix thing.  Windows no longer complains about it but there are serious problems in the Linux partitions - something that windows can't deal with - they are linux specific formats.  I really didn't expect windows to be able to fix those.  I tried various things to try to get ddrescue to read it but there were lots of issues.  Not worth the hassle.  I am letting fsck have a crack at it.  It's been running a couple hours.  If that doesn't work I will just start over.

---

### Post by Bucky Ball on 2016-05-14
If you can actually access it in Ubuntu, even if you can't access those partitions on it, try launching Gparted, unmount partitions, delete partition table then create a partition and see if it works ok. 

Is this a regular sd card or a larger sdxc card?

---

### Post by JimLS on 2016-05-14
I am ready to give up on this.  It's a 8 Gig card.  I have used Gparted a little.  I take it you are suggesting some like this?  I might give it a try.

[URL="http://gparted.org/h2-fix-msdos-pt.php"]http://gparted.org/h2-fix-msdos-pt.php

[/URL]

---

### Post by Bucky Ball on 2016-05-14
It's in the repos. Just install it from Software Centre or whatever package manager you are using. Right click partitions, unmount, click I think 'Devices' and 'Create partition table'. That will delete anything on it and create a new partition table. From there, create partitions.

---

### Post by JimLS on 2016-05-14
Bucky Ball,

I know where gparted is.  In fact it is installed.  But it hangs on startup (no error message) if the problem sd card is connected.  I only waited a few minutes so it might eventually figure it out but I doubt it.  You said you suggestion "will delete anything on it" and my whole point was to try to recover the data.

Let's go another direction...  If I make another, same size card with the same partition layout  (I have the original image but the programs are unconfigured) can I somehow take the partition table from that sd card and put it on the bad sd card, leaving the data in the partitions alone?
I tried gpart and got this:
gpart /dev/sde

Begin scan...

* Warning: short read near sector(134788), 52224 bytes instead of 66048. Skipping...

* Warning: read error (EIO) near sector(134890), skipping...

---

### Post by Bucky Ball on 2016-05-15
You could try Cloning the partition or drive to another using something like Clonezilla, fsarchiver or dd (be VERY careful with the last one as it's nickname is disk destroyer: it takes no prisoners if you make a wrong move!).

---

### Post by sudodus on 2016-05-15
Try cloning with ***mkusb***. It wraps a safety belt around dd :-)

See this link: [mkusb](https://help.ubuntu.com/community/mkusb)

```
sudo -H mkusb /dev/sdx
```

where x is the drive letter for the SD card, for example /dev/sdb or /dev/sdc.

***mkusb*** will let you identify and select the correct target drive.

---

### Post by Bucky Ball on 2016-05-15
> **sudodus said:**
> Try cloning with ***mkusb***. It wraps a safety belt around dd :-)

Doh! I always forget mkusb! Yes, try that. I should use it a few times myself so it sticks in my (short) memory. :| ;)

---

### Post by JimLS on 2016-05-15
I have done more messing around with this than it is worth.  I have been doing a bit here and there as I have time so haven't been working on this continuously but still a lot of time.  Now to create a new image on a new sd card and make sure I have a back up this time.  Should have done that before. And put a battery UPS on the Beaglebone so it can shut down properly on power loss (or possibly set a serial link to the UPS so it knows when it is going to shut down.

---

### Post by Bucky Ball on 2016-05-15
If you're throwing in the towel on this one, please mark the thread as 'solved' to save others some time. Good luck. :)

---

