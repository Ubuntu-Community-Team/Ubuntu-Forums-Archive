---
title: "Boot and shutdown errors"
date: 2013-11-21
forum: General Help
---

### Post by spreafab on 2013-11-21
Sorry to step in,
but I am also experiencing nightmares here.
I was working normally this evening, and I received the notification of 13.10 available. There were also a lot of other updates available.
At the end of the (many) updates (it was quite a bit the machine was off, before) I was requested to reboot.

Since then nothing more is working.

The last error screen I have now, after several REISUB is the following:

```
[487.940765] ata 3.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xe frozen
[487.940843] ata3: SError: {PHYRdyChg CommWake Dispar LinkSeq TrStaTrus}
[487.940909] ata 3.00: failed command: FLUSH CACHE EXT
[487.940979] ata 3.00 cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[487.940979]              res 40/00:ff:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
[487.941053] ata 3.00:status: {DRDY}
[487.941119] ata3: hard resetting link
[487.941178] ata3: nv: skipping hardreset on occupied port

```
Sorry if there are mistakes. The machine is completely out of control (no possibility of switching it off normally, no network connectivity), and I had to copy these things on a sheet of paper and type them here with the laptop (windows...).

Sorry, but I start having serious doubt about this distribution. I already had to re-install the OS completely due to a similar situation, where you start getting "chinese-like" (sorry, no pun intended: it's just to say something completely out of my reach!) messages and you get messed up and up again.

This is the third month I re-turned to Linux after several, several years. Usability is still a big problem. If Microsoft stuff would behave like that (two hard and complete failures in three months, without having "made" anything strange but accepting automatic updates) with the kind of very very very intensive use I (and millions of other people) make of it every day, that company would not exist anymore. Unfortunately this frequency of accidents is not tolerable for something that doesn't want to be "amateurial".

Very surprised, unfortunately!

BTW: the only way to shut down the computer properly, after the x-th REISUB, was to log on into Win7 (a demo-unregistered copy) and make a shutdown. Windows rescuing Linux! (unbelievable)

---

### Post by oldfred on 2013-11-21
Moved to your own thread. Issues are not really related and trying to post different suggestions for two users get very confusing.

Your drive is frozen, is this an SSD?
[487.940765] ata 3.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xe [COLOR=#ff0000]frozen
[/COLOR]From live installer
Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump
sudo ls /dev/disk/by-id

More info on frozen
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)

---

### Post by spreafab on 2013-11-22
Thank you for your action oldfred.

Just a couple of questions, anticipating that I am not a person who is interested in spending hours and hours for taking care of maintenance of the operating system, but would rather like to spend the (very precious) time in productivity:

1.The SSD Memory Cell Cleaning procedure you linked me to says "[COLOR=#000000][FONT=sans-serif]Using this procedure will destroy ALL data on the SSD and render it unrecoverable by even data recovery services! Users will have to repartition the device and restore the data after completing this procedure!"

Therefore: which is my convenience? Making it or simply re-install Ubuntu from scratch?

2. How was it possible that my computer was reduced in such a status by a simple software update initiated by Ubuntu? My only mistake was accepting the update "proposal"?

As soon as I manage (not earlier than this evening), I will try the hdparm procedure you suggest, as soon as I manage to get to a console. The only problem that I see is that, being now the machine completely out of the web (I think network drivers do not get loaded properly), I shoud then copy by hand any possible message and retype it here (which is a very annoying, error-prone, time-consuming practice). Any suggested alternative?

Thanks in advance to all the mighty people here around proposing eventual solutions.[/FONT][/COLOR]

---

### Post by fantab on 2013-11-22
Sometimes the only and the best way is the hard way.

Simply re-installing Ubuntu or for that matter any OS, is not going to 'cure' your SSD.
It is quite probable that your SSD already had its issues, updates have perhaps only hastened the effects of the problem because of lots of writing during installing upgrade.


SSD's have a faster read/write speed but that does not necessarily mean they don't have any limitations. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives#Overview](https://wiki.archlinux.org/index.php/Solid_State_Drives#Overview)

So what you have is an SSD related issue and OS has nothing to do with it.

If the SSD is under warranty, see if you replace it. But AFAIK you will only get a refurbished piece as replacement.

BACKUP all your important DATA before you get on with fixing the issue. 

Good Luck...

---

### Post by spreafab on 2013-11-22
People,

thank you very much for your support and input: I really appreciate.

But, now that I have googled a bit of your acronyms and explanations (sorry sorry: I am very far from any hardware or low-level programming expertise, being more a "power user" of mathematical/statistical software and hobbyst high-level programmer) I now realize that:

* I have probably no Solid State Drive at all: all what I have is "rotating"
* I have probably no UEFI, because I see a very nice "BIOS" screen when switching on my machine.

So, I am sorry, but I don't fully understand what your comments relate to. I am in this moment far from my sick machine, but I fear the problem is something else.

Suggestions for diagnostics?

Thanks in advance.

---

### Post by fantab on 2013-11-22
Ok.

Boot with Ubuntu DVD/USB and 'try Ubuntu without installing'... Then tell us if you have any difficulty.
(If you are right about you not having either SSD or UEfI then, it could be kernel error, its possible).

If you are able to boot with Ubuntu DVD/USb then from desktop open terminal [Ctrl+Alt+T], run the following command and post the output of the following:
```
sudo parted -l
sudo fdisk -l
```

Write about your machine? Laptop? Desktop? Brand and Model? year of purchase? Did the machine come pre-installed with any OS?

---

### Post by oldfred on 2013-11-22
I was not suggesting the memory cell clearing but the info in that article on frozen and that it had some more info on it. I am not sure I fully understand why a drive gets into frozen status and it seems like there is not one way to clear that.

Once drive is unfrozen then you may just need some minor repairs, fsck or others. Or it just could be drive failure that is a coincidence.  From Disk Utility or Disks, if you click on drive what does Smart Status show on drive. It has lots of detail but all I really know is passed is ok.

---

### Post by spreafab on 2013-11-22
Hallo fantab,

Thanks so much!
Here the data:
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103SI (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type      File system  Flags
 1      1049kB  106MB   105MB  primary   ntfs         boot
 2      106MB   277GB   277GB  primary   ntfs
 3      279GB   664GB   385GB  primary   ntfs
 4      664GB   1000GB  337GB  extended               lba
 5      664GB   1000GB  337GB  logical   ntfs


Model: ATA WDC WD5000AAVS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  250GB  250GB   primary   ntfs            boot
 2      250GB   500GB  250GB   extended
 6      250GB   496GB  246GB   logical   ext4
 5      496GB   500GB  4292MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 



```

and

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82983c54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   541861887   270827520    7  HPFS/NTFS/exFAT
/dev/sda3       543959040  1295986527   376013744    7  HPFS/NTFS/exFAT
/dev/sda4      1295986688  1953521663   328767488    f  W95 Ext'd (LBA)
/dev/sda5      1295988580  1953521663   328766542    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd92629d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488384063   244192000+   7  HPFS/NTFS/exFAT
/dev/sdb2       488384510   976771071   244193281    5  Extended
/dev/sdb5       968388608   976771071     4191232   82  Linux swap / Solaris
/dev/sdb6       488384512   968388607   240002048   83  Linux

Partition table entries are not in disk order



```

News about the computer: this is a desktop, I bought it on ebay as a number crunching mule (data mining) from a guy delivering it without OS (just a non-activated windows7). It has 3.9 GB memory, it is a quadcore (AMD Athlon(tm) II X4 630 Processor × 4 ) has a Gallium 0.4 on NV96 graphic device, and mounts ubuntu 64 bits. It has no brand (the seller put it together, motherboard is ASRock N68C-S.
Does it help you?
Thanks again

---

### Post by spreafab on 2013-11-22
Thank you oldfred.

I found and opened the disks utility (while I am logged from the DVD). Unfortunately SmartStatus is deactivated, and in the menu I don't manage to activate it (greyed out).

---

### Post by oldfred on 2013-11-22
It may be because it still is frozen?
I thought all new drives supported Smart Status.

Have you tried total cold reboot or full shutdown?
Have you check BIOS for hard drive settings? Is drive shown correctly in BIOS?

---

### Post by spreafab on 2013-11-22
Hallo Oldfred, 
thank you for assistance.
Yes, I have tried a cold reboot and several full shutdowns.
Drives are both shown correctly in the BIOS: no apparent problem. (But this seems to be the case also for the parted and fdisk outputs above, as far as I can understand).

I have the impression that the errors on the drives are a consequence and not the cause of the weird problems I am having now.

Currently the situation is that:
* I cannot normally boot in any operating system straigth (event Windows 7 is not doing it anymore)
* I always get into the grub. If there I select recovery mode (yes, I tried already to repair anything possible there, comprising a resetting of grub) and then I simply chose the option of resuming normal booting, I immediately come to the normal login.
* I can then access the system normally. This was also the case after having called the BIOS screen.
* The system I have access to is anyway just "half-working". For instance it is impossible to get network connectivity (whereas the hardware is all in place and working: boothing from the installation CD allowed me to post from the machine the previous messages).

I am very puzzled for this behavior.

In the meanwhile I have also run a memory test. No problem detected after 2 x complete runs.

---

### Post by oldfred on 2013-11-22
Windows is a separate hard drive, so that then says something else in system.
And if you cannot get on network, it that perhaps the issue?
Is boot real slow when you are booting, and then are dmesg error messages related to network or enablement of Ethernet card?

Note I am grasping at straws as I do not know exactly what is happening or in other words have a good suggestion on what to do.

---

### Post by spreafab on 2013-11-22
> **oldfred said:**
> 

Note I am grasping at straws as I do not know exactly what is happening or in other words have a good suggestion on what to do.

Hallo oldfred,

Thanks so much also for your sincerity and opennes.

On the same stream: I fear the best way to go now is simply re-install.

But I am a bit worried, because this is the second time since I have my PC (three months?) and mounted Ubuntu.

Would you say there could be some improvement in "robustness" of the system with some other "dialect": Kubuntu, Lubuntu, Xubuntu? I read around that, even if superficially just the desktop environment changes, they are really other "stuff" for other aspects. In particular there was an article describing sort of weird things like mine on upgrading to Ubuntu 13.04, while, at the same time the similar upgrade to Kubuntu and Xubuntu 13.04 were a dream.

Any opinion/experience? It is all Canonical after all, or? :confused:

---

### Post by oldfred on 2013-11-22
I did upgrades from 6.06 thru 9.04 with 32bit and often various issues, back then nVidia was always an issue. 
But I wanted to convert to 64 bit with 9.10 and that had absolutely no issues as a clean install.
Also about that time I go a new larger hard drive and just make every new install a new 25GB partition. I can then go back and get something if need be, but all data is in separate data partitions and I do not customize many settings in /home.

So a new clean install for me works better. I in effect housecleans out logs and old settings, but if you have customized a lot you may want to reuse /home which does have a lot of your user settings.

Underlying system is the same in all flavors of Ubuntu. It just is the desktop, gui & supporting default applications that are different.

If you have a spare 25GB (which out of 1.5TB total) you might, I would then just install another copy in another partition and see what happens. My 640GB drive now has so many 25GB / partitions I cannot keep track and have to turn os-prober off or it goes beserk. Most are now old/obsolete and need housecleaning.

---

### Post by spreafab on 2013-11-23
Hallo Oldfresd and all the friends here.
Thank you very much for all your assistance.
I will leave the thread open for eventual last thoughts from somebody else and then "resolve" it.

The "resolution" unfortunately is nothing of which ubuntu can be much proud. Reading all the posts here and looking around the web quite intensively, I have come to the conclusion that this distribution is not what I would like to use in the future.
I must say that I am quite impressed by Mint, and that I appreciate so much both the Desktop interface they offer (it's a question of personal preferences, but compared to Unity, for me personally, this is 100 fold better - any of those offered there -) but first and above all the policy of less frequent and more tested updates, which are never suggested as "something that you should immediately do", and even ranked according possible risks.

How things get done there is quite impressive. Just following you, Oldfred, from their distribution DVD image - installation disk, I launched Disks, and, what was not possible, for whatever reason, under ubuntu, was immediately possible with Mint DVD image: SMART tests were possible, and disks are OK. So strange, but unfortunately I have not a lot of time and resources for digging too much into details and see what the hell happened with ubuntu during and after the last suggested (and unfortunately accepted) update.

What is important for me is not becoming a "scientist" of intricacies and background of low-level operating systems technologies, but to use a computer for my production aims. I will now install Mint, and whish me a lot of work with it.

Sorry and bye

EDIT: one day later. My PC is up, running, connected to the web and w/o disk problems. Mint looks awesome. I close the thread. My problem is solved.

---

