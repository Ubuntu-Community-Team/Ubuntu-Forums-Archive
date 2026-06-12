---
title: "[SOLVED] Make a partition active with Alternate"
date: 2007-08-24
forum: General Help
---

### Post by poisonborz on 2007-08-24
Hi,

For some time, I've been dual-booting WinXP and Ubuntu. Now, that I'm reinstalling my system, I've tried to restall WinXP - but (according to some comments on other forums) it won't install, since Ubuntu's partition is the active partition (the installer just says, the partition is not Windows XP compatible)

Is there a way to change a partition to active from the alternate cd command line? (I can't do this with the XP install, to get command line/fdisk, I would need a floppy for that, wich I don't have - also, because I've formatted the XP drive, GRUB won't load, so I also can't use prev Ubuntu install)

---

### Post by bernied on 2007-08-24
Use fdisk, it should be on the install cd.

---

### Post by poisonborz on 2007-08-24
As I wrote above, to get to the command line in XP install, you need to have a floppy drive (or at least on my installer) That's why I've asked if this could be done with the Ubuntu Alternate cd.

---

### Post by Herman on 2007-08-24
You can use [Super Grub Disk]("http://geocities.com/supergrubdisk/") if you have one, to activate a partition, or any GRUB CD or Floppy disk or USB. GRUB's 'makeactive' command sets the boot flag on a partition.

Another way to do it is to use [GParted -- LiveCD]("http://gparted.sourceforge.net/") if you have one of those, or probably any  hard dsik partrition editing softare, should be able to manage the flags for any partitions.

The Ubuntu 'Alternate' CD can do that too, you would boot through the normal hardware detection phase and then select manual partitioning, then the partition you want to modify. set the boot flag, select 'done setting up the partition', and then I'm not certian what will happen after that.
Probably you would select 'write the changes to disk', and then get some kind of red screen with a warning message about not having formatted a partition for '/', but you can probably abort the installation and reboot. I guess that's probably what will happen, well, something like that anyway.

I don't have a computer plugged in at the moment that has Windows in it and is mine to experiment with or I'd run through it myself and tell you exactly for sure. Unless you want to wait until I plug in a test box and try running through it first for you. Actually it should be perfectly safe to just go ahead and do it. The 'Alternate' CD is very useful, it's just a bit embarassing if you get one of those red warning screens coming up. Mostly they're not too serious, like the little boy that called 'wolf'.

Regards, Herman :)

---

### Post by poisonborz on 2007-08-24
Thanks for the extensive reply...

I did that, flagged the partition for boot, but somehow the whole mbr got messed up. Partition magic (which I could have used for the whole thing, stupid me) shows the whole drive as "BAD". Windows can still see one partition that was untampered, but the main 80 gb partition is only shown as an unformattable 2mb drive... I have 121 gb of important data on the drive, so I can't format the whole thing... I wonder if there could be a way to repair the mbr in this state...

---

### Post by bernied on 2007-08-24
> **poisonborz said:**
> As I wrote above, to get to the command line in XP install, you need to have a floppy drive (or at least on my installer) That's why I've asked if this could be done with the Ubuntu Alternate cd.
fdisk is also a linux application.
It should be on the Ubuntu live-cd.

There might also be cfdisk, which you might find a little easier to use.

---

### Post by bernied on 2007-08-24
If you know where the partitions were, you can recreate the partition table with fdisk - this does not change data on the disk. There are other utilities that can find or guess where the partitions were, I'll have a look about and see if I can find one.

Try not to do anything that actively changes the disk, until you are sure what needs to be done.

---

### Post by bernied on 2007-08-24
Maybe [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) is the medicine you need.

---

### Post by Herman on 2007-08-24
>  I did that, flagged the partition for boot, but somehow the whole mbr got messed up. I'm sorry about that. :(
> Partition magic (which I could have used for the whole thing, stupid me) shows the whole drive as "BAD". Hmm, in my personal opinion,   you should stick with one brand of hard disk partritioner and avoid even opening any partitioners that are designed for mainly for use with proprietary software, even just to take a peek at your partitions. I suppose that's just a matter of opinion though. I really wish I knew the facts to explain exactly why it is I think so.
>  		Maybe [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is the medicine you need.I agree with bernied, here's a web page showing examples of how to use TestDisk in case that will help you, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstrated
Once again, sorry about your problem, I never would have imagined that just setting the boot flag on a partition could bork your whole partition table. :(
Good luck with recovering it again,
Regards, Herman

---

### Post by poisonborz on 2007-08-24
Thanks, TestDisk is awesome - it quickly restored everything, XP installed on the partition without a problem, and ubuntu will follow :)
(I wonder why the boot flag was a problem.. I'm sure the installer didn't touched anything else)

---

### Post by bernied on 2007-08-24
I love a happy ending

---

### Post by Herman on 2007-08-24
> I love a happy endingMe too! :)

Regards, Herman :)

---

