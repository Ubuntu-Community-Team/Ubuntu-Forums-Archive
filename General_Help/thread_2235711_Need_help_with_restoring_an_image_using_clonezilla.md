---
title: "Need help with restoring an image using clonezilla"
date: 2014-07-22
forum: General Help
---

### Post by cannon_dt on 2014-07-22
Hi,
Months back, from a dying hard drive, I managed to do a backup using clonezilla of my hfs+ Mac Lion partition. The image now resides on my external hdd.

Now on my new hdd, I have created a partition formatted as hfs+, here is my fdisk output:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   195311615    97654784   83  Linux
/dev/sda2       195313662  1722839039   763762689    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3      1722839040  1953523711   115342336   af  HFS / HFS+
/dev/sda5       195313664   203216895     3951616   82  Linux swap / Solaris
/dev/sda6       203218944   593842175   195311616   83  Linux
/dev/sda7       593844224  1013274623   209715200   83  Linux

When I try to restore my image onto the newly created sda3, it never gets listed as the target partition. Once I select the image from the external HDD, in the next step when I select the target partition sda3 does not show up - it shows only sda1, sda6 and sda7.

What am I missing? Please help, with great difficulty I managed to get a Mac Lion set up and backed up, if I am unable to restore it would be a lot of effort gone to waste.

Thanks,
Ananth

---

### Post by Mark Phelps on 2014-07-22
It's been a while since I did a CLonezilla restore, but from what I remember, you can only select a target Drive -- not a target partition. From what I remember, it rewrites the saved partition to the same location on a drive from which it was saved, in other words, if you saved sda2, and you then go to restore that to sdb, it will become sdb2, overwriting anything already there in the process.  But, as I say, it's been a while and maybe Clonezilla restores are more flexible today.

---

### Post by cannon_dt on 2014-07-22
But in the options just like savedisk and saveparts there is a restoredisk and restore parts. So it certainly supports the restoration of targeted partitions. 
Also how come the other partitions are being shown as potential target partitions (even though they are not the hfs ones)

All so sad :(

---

### Post by cannon_dt on 2014-07-30
Hi,
Months back, from a dying hard drive, I managed to do a backup using clonezilla of my hfs+ Mac Lion partition. The image now resides on my external hdd.

Now on my new hdd, I have created a partition formatted as hfs+, here is my fdisk output:
```
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 195311615 97654784 83 Linux
/dev/sda2 195313662 1722839039 763762689 5 Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3 1722839040 1953523711 115342336 af HFS / HFS+
/dev/sda5 195313664 203216895 3951616 82 Linux swap / Solaris
/dev/sda6 203218944 593842175 195311616 83 Linux
/dev/sda7 593844224 1013274623 209715200 83 Linux

```
When I try to restore my image onto the newly created sda3, it never gets listed as the target partition. Once I select the image from the external HDD, in the next step when I select the target partition sda3 does not show up - it shows only sda1, sda6 and sda7.

The reason for this I realize is that when I saved the image the hfs+ partition was sda5. So the image seems to have that information hard coded in it and hence no sda3 comes up while restoration.

So now I need to rename the sda3 to sda5. But my current hdd as sda5 as Linux swap. So what should I do to get the sda5 name onto the hfs+ parition? 

Can I rename the swap (if I do would that cause problems?), then the hfs+ and if so how can I do this? I desperately need help, so can you guys guide me

Thanks
Ananth

---

### Post by coffeecat on 2014-07-30
Threads merged. Please do not start a duplicate thread when you still have an open one which you can bump if needed.

You appear to be trying to restore a cloned MacOS partition onto a hard drive with a MBR partition table. What hardware are you using?

---

### Post by cannon_dt on 2014-07-30
Sorry, I thought they were different topics, hence started a new one. Apologies for the same.

I had Mac OS Lion on my dead HDD which I used to boot into when required. Mint was the distro I use, using GRUB I used to log into Lion when I wanted, so I had it set up only in GRUB (I am assuming this means no MBR entry right?, I am not sure)
Hardware - a new HDD with the structure as show above, Linux Mint as my primary OS. 
Is there any other information you need wrt hardware?

I read over at another forum that it is the partition name mismatch that is causing the issue. I checked the my image folder has almost all file names starting with sda5. That seems to be the most potention cause, hence the help to change partition names.

Ananth

---

### Post by coffeecat on 2014-07-30
By hardware, I was asking you what computer you were using, i.e. whether or not it was an Apple machine. Now I see from this earlier thread (which I have now closed) that you were setting up a hackintosh partition:

[http://ubuntuforums.org/showthread.php?t=2231606](http://ubuntuforums.org/showthread.php?t=2231606)

In which case I'll assume that this clonezilla image is of your hackintosh partition and that you are not using Apple hardware. The Apple EULA is clear - you may not run MacOS on anything other than Apple hardware. Our forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules") is clear:

> We do not support circumventing TOS, EULA, etc here. 

Thread closed.

---

