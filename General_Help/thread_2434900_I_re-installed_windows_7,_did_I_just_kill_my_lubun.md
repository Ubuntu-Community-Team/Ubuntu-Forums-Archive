---
title: "I re-installed windows 7, did I just kill my lubuntu partition?"
date: 2020-01-13
forum: General Help
---

### Post by hurtstotalktoyou on 2020-01-13
I knew re-installing Windows 7 would kill grub, but that could be fixed.  Apparently though the Windows 7 installer screwed with my partitions.  When I boot into a live usb lubuntu I get this from fdisk -l:

```

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2           206848 2456515268 2456308421   1.1T  7 HPFS/NTFS/exFAT
/dev/sda3       2456516608 2457599999    1083392   529M 27 Hidden NTFS WinRE
/dev/sda4       2457604094 3907028991 1449424898 691.1G  5 Extended
/dev/sda5       3898644480 3907028991    8384512     4G 82 Linux swap / Solaris

```

The "extended" partition is where lubuntu is supposed to be.  I have some important files there.  Any chance I can recover them?

I just want the files, then I can re-install lubuntu.

Sorry to be so whiny.  I'm just very bummed about this.

---

### Post by howefield on 2020-01-13
Installing Lubuntu over the existing partitions without marking them for formatting should leave your /home folder intact, but without a backup of your important files it would be reckless to trust them to that. Can you boot from Live media and mount the relevant partition and copy over your files ?

---

### Post by hurtstotalktoyou on 2020-01-13
Well, what used to be the lubuntu partition is now showing up as the "extended" container (sda4).  But I've read that extended containers aren't mountable, because they're not really partitions, but containers.

---

### Post by coffeecat on 2020-01-13
Hi

The Windows installer has been randomly deleting Linux logical partitions for far too long. Fortunately, it probably hasn't deleted the information in the now lost partition - just the entry in the partition table. Here's from a thread from about 6 years ago:

[https://ubuntuforums.org/showthread.php?t=2217973&p=12994041&viewfull=1#post12994041](https://ubuntuforums.org/showthread.php?t=2217973&p=12994041&viewfull=1#post12994041)

Oldfred's suggestion in the post following to use testdisk would be the way to go. When I have time, I'll search for some earlier posts on this subject, in case there is something there that might help you.

---

### Post by hurtstotalktoyou on 2020-01-13
Thanks it sounds like testdisk is my best option.  I'm going to search for more info, but in the mean time, if anyone has any experience with testdisk please feel free to chime in : )

---

### Post by dragonfly41 on 2020-01-13
This case study is another argument for just keeping Windows and Ubuntu in separate drives, not single shared drive.
We have all shared Windows host drives in this way but is the hassle worth it to save a few dollars/pounds in outlay for an external drive?
I am guilty of this practice but I have started to migrate my Ubuntu onto an external USB SSD in a dual bay docking system.
Now the advice is that you will need to invest* anyway* since the basic testdisk rule is that you cannot save recovered files into the same device you are trying to recover. You will overwrite the very files you hope to recover. And remember that all files that were genuinely "deleted" before this mishap will also be recovered by testdisk. You will have a large pile of files to sort through.

One approach (there are several alternative strategies) would be to purchase **two** external USB drives in USB drive containers, **at least** equal in capacity to the one you have.
The first drive will be used to clone the existing drive using LiveUSB+Clonezilla for this task.
The second drive will be formatted to receive any recovered files from the testdisk run.

Having cloned the host (internal) drive /dev/sda into /dev/sdb, install testdisk in the (non persistent) LiveUSB.
Now you can use testdisk to recover /dev/sdb/ and save into partition in /dev/sdc.
The reason for this cloning approach is to retain your corrupted drive as "master" and work on recovering the cloned drive, instead of the "master".

You might also experiment by installing R-Linux (from R-Studio) into LiveUSB to see if you can recover ext4 files from /dev/sda/.
R-Linux can be installed in either Windows (persistent) or Ubuntu LiveUSB (non persistent).

But again - keep notes of the installation commands since some apps require to be reinstalled in a non persistent LiveUSB every bootup session.

At the end of this painful recovery exercise you might consider reassigning your drives:
/dev/sda/ use for Windows only
/dev/sdb/ use for Ubuntu only
/dev/sdc/ use for Ubuntu backup only (perhaps using Timeshift).

For me, I find that a dual bay USB 3 docking station (such as from StarTech) is very useful for holding /dev/sdb and /dev/sdc.
Avoids messing with the innards of my PC to squeeze in another drive.

And I suggest that you browse the testdisk and photorec forums.

**[Later edit]**

I will add that recently I had a corrupted partition table in one of my three drives with message "bad GPT partition, invalid signature" and I quickly corrected this by applying testdisk in a LiveUSB session.  Select partition table type:
if MBR select "Intel"
if GPT select "EFI GPT"

and then Analyse, try to locate partition.

It was a matter of changing D to P in menu and rewriting and I was back in business.
So in some cases a purchase might not be needed.

Another ploy is to use LiveUSB and run GParted and try Device > Attempt Data Rescue.

---

### Post by hurtstotalktoyou on 2020-01-13
Good news!  I tried testdisk and I believe I have recovered my partition perfectly. Well, almost perfectly. (Grub2 won't install for some reason so I can't actually boot into it.)

But unfortunately being a newbie at testdisk, I accidentally killed my windows partition now!  But that's no big deal, there were no files on it.  I just have to go through the hassle of reinstalling it.

---

### Post by mastablasta on 2020-01-13
next time (and unless you need win 7 for gaming or some GPU intensive tasks) just install it inside virtualbox or similar. much less hassle and no way you would destroy partition with that install.


+ always backup before messing with partitions. in fact you should keep data backed up anyway. but before messing with partitions and disks it is best to do a disk clone (e.g. with clonezilla). so if anything goes wrong you can easily restore to previous situation.

---

### Post by mörgæs on 2020-01-13
Windows 7 is out of support. Are you sure that you want it around?

---

