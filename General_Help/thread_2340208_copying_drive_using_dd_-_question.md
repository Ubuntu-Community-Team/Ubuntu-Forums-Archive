---
title: "copying drive using dd - question"
date: 2016-10-16
forum: General Help
---

### Post by 20GT on 2016-10-16
I want to copy one entire drive to another, remove the original drive and boot from the copy. I'm not very knowledgeable about Linux or computers in general. I researched and found that the dd command was probably the way to do it. My OS is Ubuntu16.4LTS. The destination drive doesn't show up as mounted in Ubuntu but it shows in my hardware profile.


**Is that going to matter when using dd?**


my full [hardware profile]("http://www.funsun321.com/hardwareprofile.html")




original drive
```

id:	scsi:0
physical id:	1
logical name:	scsi0
capabilities:	emulated
**********
id:	disk
description:	ATA Disk
product:	HDS728080PLAT20
physical id:	0.0.0
bus info:	scsi (at)0:0.0.0
logical name:	/dev/sda
version:	A27A
serial:	PFD8T5SXRBY6VX
size:	74GiB (80GB)
capabilities:	partitioned partitioned:dos
configuration:	
ansiversion	=	5
logicalsectorsize	=	512
sectorsize	=	512
signature	=	54eda6e3

```




destination drive
```
id:	scsi:1
physical id:	2
logical name:	scsi2
capabilities:	emulated
**********
id:	disk
description:	ATA Disk
product:	SanDisk SDSSDA12
physical id:	0.0.0
bus info:	
scsi (at)2:0.0.0
logical name:	/dev/sdb
version:	80RL
serial:	163602453113
size:	111GiB (120GB)
configuration:	
ansiversion	=	5
logicalsectorsize	=	512
sectorsize	=	512
```

---

### Post by frostschutz on 2016-10-16
Neither side should be mounted. So basically if one of them is your system disk, you should do this from a Live CD.

Using dd will duplicate UUIDs. So if you reboot afterwards and have both disks attached, it might mount the wrong ones since it can no longer identify one disk over the other. So instead of simply rebooting, it would be preferrable to shut down and remove the disk.

---

### Post by papibe on 2016-10-16
Hi 20GT.

The source drive must be unmounted too, specially if it is where the OS is.

The common practice is to use a Live media to do this. The Ubuntu installation CD/USB works well as Live media. Just select 'Try Ubuntu' instead of installation.

Here's more information about using dd as an imaging tool: [Drive Imaging]("https://help.ubuntu.com/community/DriveImaging").

Hope it helps. Let us know as it goes.
Regards.

---

### Post by 20GT on 2016-10-16
I'm booted on a live CD now

my questions still is Ubuntu can see my original drive but it doesn&#8217;t see my other drive 
when I run 
```
sudo lshw -html > hardwareprofile.html
```

its the shows both drives 



 [ATTACH=CONFIG]271658[/ATTACH]
I clicked unmount on the Ubuntu drive  it but I still see it?

what does this mean

> If you are positive that your disk does not contain any errors, you  could proceed using a larger block size, which will increase the speed  of your copying several fold.
how do I assure that there are no errors?

do I need to run this? or something different?
```
dd if=/dev/sda of=/dev/sdb status=progress  
```

---

### Post by frostschutz on 2016-10-16
Add bs=1M for speed. Understand that all data on the of= device will be overwritten.

The device names change sometimes. Make sure /dev/sda and /dev/sdb both are what you think they are (fdisk -l). Make sure neither of them shows up in the list of mounted filesystems (mount).

---

### Post by monkeybrain20122 on 2016-10-16
It is a lot safer and faster to clone your system and then  restore it in the destination. dd is kind of risky and vanilla dd doesn't have any output to report progress, that kind of makes me nervous. Also if you don't know what is going on you may have to go through some hoops to re-use your hard drive after doing dd on it , erasing the content will make the drive unusable because dd destroys the partition table and you have to recreate it, something like that IIRC. 

I wouldn't recommend dd for this especially if you are inexperienced. You can do some experiments with something less daunting like using dd to make a live usb drive first.
  
dd is a geek tool, in 2016 there are much better and safer ways to do what you want on Linux. Try fsarchiver, it is in the repo. you can clone live (i.e while using your system. use the -a and -A options in savefs) and then restore it to the destination with a live usb with fsarchiver installed on it (just use a Ubuntu live usb and install fsarchiver, since it doesn't require reboot, you don't need persistence in the live usb)
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by 20GT on 2016-10-16
> **monkeybrain20122 said:**
> It is a lot safer and faster to clone your system and then  restore it in the destination. dd is kind of risky and vanilla dd doesn't have any output to report progress, that kind of makes me nervous. Also if you don't know what is going on you may have to go through some hoops to re-use your hard drive after doing dd on it , erasing the content will make the drive unusable because dd destroys the partition table and you have to recreate it, something like that IIRC. 

I wouldn't recommend dd for this especially you are inexperienced. You can do some experiments with something less daunting like using dd to make a live usb drive first.
  
dd is a geek tool, in 2016 there are much better and safer ways to do what you want on Linux. Try fsarchiver, it is in the repo. you can clone live (i.e while using your system. use the -a and -A options in savefs) and then restore it to the destination with a live usb with fsarchiver installed on it (just use a Ubuntu live usb and install fsarchiver, since it doesn't require reboot, you don't need persistence in the live usb)
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)


I’m lost, you want me to return to my real Ubuntu (not live) and install fsarchiver?
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) doesn’t say anything about cloning?
[URL="http://www.fsarchiver.org/QuickStart"]
[/URL]

---

### Post by frostschutz on 2016-10-16
> **monkeybrain20122 said:**
> vanilla dd doesn't have any output to report progress

Yes it does (status=progress). And before that was added you could always get progress by sending a USR1 signal.

The one thing it does not handle at all well is read errors. It offers some conv options for those but they don't actually work. You have to switch over to ddrescue.

> **monkeybrain20122 said:**
> I wouldn't recommend dd for this especially if you are inexperienced.

Yes, maybe it's easier to just - re install to the new disk and then copy files over from the old one. This also lets you make new decisions regarding LVM, partition layout, encryption and what not.

dd has its pitfalls but so do other solutions. You can go horribly wrong with clonezilla, fsarchiver, rsync etc. if you do things the wrong way.

---

### Post by 20GT on 2016-10-16
ok ok ok 
the destination drive in blank, new, brand new, empty.

can't I just format and try again if it doesn't work?

---

### Post by 20GT on 2016-10-16
> Yes, maybe it's easier to just - re install to the new disk and then copy files over from the old one.

does copying files keep my programs intact?
I could just start fresh but that is not my objective

---

### Post by monkeybrain20122 on 2016-10-16
Go back to your "real Ubuntu", sudo apt-get install fsarchive. Attach a drive with a partition which you want to store your clone since you shouldn't modify the very system that you are cloning by saving its own clone there 

```
sudo fsarchiver -a -A -v savefs /path/to/where/you/want/to/store/the/clone/ubuntu.fsa /dev/sda
``` This way you can use your computer while cloning, make sure you don't modify the system while doing it (like doing updates or installing/removing software)

Here I assume your system is in /dev/sda. ubuntu.fsa  is the name you give the clone, any name is fine as long as it ends with .fsa.  To restore, you actually don't even need a live usb since you are restoring it externally.

First make sure you have partitioned the external drive you want to restore the system to so that you know where to restore. e.g /dev/sdb1
Now if the clone were saved on this same partition you need to move it, otherwise (either it was saved in a second external drive or a different partition on the drive you are restoring to say /dev/sdb2) you can just keep it where it is. If you need to move it, you can just move it back to your internal drive if you have enough space

then run 
```

sudo fsarchiver -v restfs /path/to/ubuntu.fsa id=0,dest=/dev/sdb1
```

You can speed up by using more than one threads, like -j4, in the above commands. There are other options you can check out from the link above.

Now if you want to boot this external drive on the same computer you need to modify the uuid since you already have an identical system in the internal hard drive. The boot mechanism would be confused (same would hold if you use dd) If you need to do this I can give you further info.

---

### Post by monkeybrain20122 on 2016-10-16
> **frostschutz said:**
> 
dd has its pitfalls but so do other solutions. You can go horribly wrong with clonezilla, fsarchiver, rsync etc. if you do things the wrong way.

I don't know about clonezilla but I can't see how fsarchiver could be risky, it just copies the file system without modifying it and then restores it to an already emptied partition(so it won't overwrite) the worst thing that can happen is that the clone doesn't work.

---

### Post by 20GT on 2016-10-16
The destination drive is not already partioned. 

I have no idea what it is inside.

---

### Post by monkeybrain20122 on 2016-10-16
> **20GT said:**
> The destination drive is not already partioned. 

I have no idea what it is inside.

Well then you'd better check first. You need to create a partition in ext4 big enough for your system (it can be smaller than /dev/sda1, but has to be big enough for the content, this is one thing that makes it better than clonezilla) You can do it with gparted easily.

---

### Post by 20GT on 2016-10-16
[ATTACH=CONFIG]271660[/ATTACH]

partitioned

---

### Post by 20GT on 2016-10-16
> Now if the clone were saved on this same partition you need to move it, otherwise (either it was saved in a second external drive or a different partition on the drive you are restoring to say /dev/sdb2) you can just keep it where it is. If you need to move it, you can just move it back to your internal drive if you have enough space



you are confusing the hell out of me, I thought we were cloning the old drive to the new drive?
now you want me to save it on a third drive? and then restore it to the new drive?

they are both internal
One is the old drive /dev/sda
the other is the new drive /dev/sdb

---

### Post by monkeybrain20122 on 2016-10-16
Right click the entry that says "unallocated" and choose "new" and create a partition of any size you want, you can use the whole disk since it is kind of small, or anything enough to hold your content in your system and permitting some possible grow if it is a lot less than 80G (say only 30G is used then a partition  of 50G may be ok, depending how big you anticipate the system to grow in the future) It is quite flexible. If you want you can leave out some space for a swap partition (about 1.5 x ram depending on where you want to boot it, it is only needed if you plan to boot it off computer with low ram since you won't be hibernating or suspending with an external hard drive anyway)

Now you can place the clone in the same partition and then move it else where when you restore the system to it. Now a bit of problem is your internal drive is small so if most of it is used already there may not be enough space for the clone, you may need a second external drive.

---

### Post by monkeybrain20122 on 2016-10-16
BTW you can store the .fsa file in any hard drive, it doesn't have to be formatted to ext4. Only the partition that you restore the system to have to be such formatted. So if you have a drive in NTFS you can save the .fsa there  and restore from there as well.

---

### Post by 20GT on 2016-10-16
> [COLOR=#000000]Now you can place the clone in the same partition and then move it else where when you restore the system to it. Now a bit of problem is your internal drive is small so if most of it is used already there may not be enough space for the clone, you may need a second external drive.[/COLOR]

????? I thought we were creating it directly on the destination drive and we are done
why do We have make a clone and then restore to the destination drive.
I don't have another drive

---

### Post by monkeybrain20122 on 2016-10-16
> **20GT said:**
> ????? I thought we were creating it directly on the destination drive and we are done
why do We have make a clone and then restore to the destination drive.
I don't have another drive

This is how cloning works:

origin --> clone or creating a backup copy of the system (in this case the.fsa file) in some place then,   restore the backup(i.e clone) **from** the same place where you saved it in the firs step** or some other place** --> destination. The first arrow is "savefs", by which you create the backup. The second arrow is "restfs" by which you restore the clone to the destination

Now you can create the clone in the destination in the first arrow, but then for the second arrow you have to place it somewhere else. So to avoid a second hard drive you would either have  enough free space in the internal drive so you can store the copy when you are restoring, or have a big enough destination so you can save the copy in there, but a different partition from the one that you restore to.

P.s if your original partition has enough free space, I think you can also create a folder in the system being cloned to hold the clone during the cloning and exclude it from being cloned using the --exclude= option.

P.S.S usually people use clone as a backup, it is then restored to the original partition, so they don't typically need a second drive (But I have been doing what you are trying to do here with fsarchiver so I know the requirements are a bit unusual)

---

### Post by monkeybrain20122 on 2016-10-17
Here is how you can get away with only one external drive. 

While your system is 80G (even if full) chances are most it is user data. Your core system is probably less than 15 G. The rest are user data (Videos, books, Music etc)So you can create a clone for just the core system which is very small, restore it to the external drive and then copy your data over.

so first use gparted to create a small partition on the external drive (say /dev/sdb2) to hold the .fsa file, since your original system is only 80G and the external is 110G and the clone of the core system is unlikely > 30 G (probably not even half of it) you have enough room

Before you do the cloning make sure you have cleaned out your trash and delete all the junks you don't need such as the system cache and unneeded localisations and language packs. I recommend using bleachbit, run it as administrator, check all the boxes under APT, under System check the boxes cache and Localizations, check Trash, rotated logs amd Temporary files, leave the rest alone. Bleachbit is in the repo.

Now the savefs command will be something like this, use the exclude option to skip directories that store only user data, feel free to add to the list.

```
sudo fsarchiver -a -A -v savefs /media/username/storage/ubuntu.fsa /dev/sda --exclude=tmp --exclude=Music --exclude=Pictures --exclude=Documents --exclude=Videos
```

Here "storage" is the name of your /dev/sdb2. If you don't give it a  name it will show up as some number. You can see it by plugging it into  your Ubuntu system and then open it with the file browser see what shows  up on top.

Now restore the .fsa you just saved to /dev/sdb1

```
sudo fsarchiver -v restfs /media/username/storage/ubuntu.fsa id=0,dest=/dev/sdb1
```


Cloning would take less than 10 minutes and restoring less than 5 for a small job like this, all the while you can keep on using the computer when fsarchiver does it work (just remember don't install/uninstall or update while cloning)

When finished, you can use gparted to delete /dev/sdb2 and expand /dev/sdb1 to cover the space. Then move your data over.

---

