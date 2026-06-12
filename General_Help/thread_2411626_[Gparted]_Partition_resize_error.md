---
title: "[Gparted] Partition resize error"
date: 2019-02-01
forum: General Help
---

### Post by fabma on 2019-02-01
Hi,
I need help for a problem occurred during partition  resize. I was extending the second partition from 250 GB to 300, but the process suddenly stopped when 20 GB were already moved (it was in input/output error). After a reboot, I can open the partition (size now is 300 Gb), and file and folders structure is intact. But some files (they are all audio files) won't open (they can be copied and pasted in another directory, but they cannot be opened); some files can be opened, but the player plays pieces of other files. 
Unfortunately I have no backup :(
What can I do? Thanks for your help

---

### Post by Impavidus on 2019-02-01
I'll spare you the lecture on backups as you already undestand that. What happened is that the information on the directory tree and the list of all files was moved, but part of the contents were not moved, so the contents are now at a different spot in the partition (relative to the start of it) than before and the references to the file contents are wrong. So, the contents of your files are now read from hard disk sectors containing the contents of other files or just random data. If this happens to be an audio file too, of the same format and properly aligned, it will be played to get your mixed audio fragments. If not properly aligned or if the first piece, containing headers, is pointing to some random data, the file is considered corrupt and won't play at all. I must say the effect is interesting.

Don't use the drive. Make an image of it and try file recovery tools on the image. Those tools may be able to find the pieces of files that belong together.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I don't know what caused this. I wouldn't be surprised if your hard drive were failing.

---

### Post by fabma on 2019-02-01
Thanks for your explanation. I think that this happened due to a usb cable problem: the drive is a 2 TB WD in a 2.0 usb box. S.M.A.R.T. is regular.
I tried Testdisk, but it says that there are no problems or deleted files (this does not surprise me, considering your explanation).
So I'm trying Photorec: it started with the files that I can play with no issues. I think that they are the files Gparted moved to the new spot in the partition, so they are located correctly. I hope it can recover the other files. But Photorec doesn't restore the correct filename and its position in subfolders. Considering this particular problem, wich software can be more suitable among those of the link you posted?

---

### Post by Impavidus on 2019-02-02
photorec scans the disk for fragments of files without assuming there's any useful information in the inode table or anywhere else, so it cannot reconstruct filenames. But it may find your files.

The interesting thing is that the fragments of your files are either where they are supposed to be, or at a fixed offset from this point. Someone with detailed knowledge of the filesystem may be able to come up with a tool that uses this information to recover your files with their names and directories. Unfortunately, I don't know very much about the internals of filesystems, so I don't know how to write such a tool myself. Don't throw the image of the filesystem away too soon.

---

### Post by fabma on 2019-02-02
Can the MFT Repair function in Testdisk ([http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)) help me? I was expanding from 250 to 300 GB the second partition of the drive (taking 50 GB from the first partition), and Gparted wrote only 20 GB. So the old MFT could not be overwritten. Do you know if Testdisk can recover the old NTFS boot sector with its MFT? In this way I could save the first 20 GB from the actual situation before this recovery; and, after the NTFS boot recovery, the other 180 GB.
Or it's a waste of time?

---

### Post by dragonfly41 on 2019-02-02
There are some users who have managed to extract metadata from files in their efforts to recover photos.

Here is [one recent discussion]("https://ubuntuforums.org/showthread.php?t=2410278").  Perhaps metadata in your audio files might be searched using jhead? Just musing.

P.S. Another thought. If you launch GParted, scan your drive, and select the culprit partition then under Device there is an option Attempt Data Rescue.  You can read more by going to GParted > Help > Contents.

However I am wary about suggesting this experiment since you have no backup.

---

### Post by fabma on 2019-02-02
Unfortunately there are no metadata in those files. The files had a precise order given only by the name.

> **dragonfly41 said:**
> 
P.S. Another thought. If you launch GParted, scan your drive, and select the culprit partition then under Device there is an option Attempt Data Rescue.  You can read more by going to GParted > Help > Contents.

However I am wary about suggesting this experiment since you have no backup.
I didn't try this function thinking that it will found a file system, but the new one, reading files in the wrong spots of the partition. The partition, infact, can be mounted. Or it works in other way? The online manual talks only about difference between file systems found / No file systems found.

---

### Post by fabma on 2019-02-02
An update. I'm analyzing Photorec results. The first folder starts with some files; those files (20.0 GB) are duplicated after a while, so they are the files Gparted moved. Assuming that "PhotoRec uses the logical sector number to create the filename" (from Photorec Faq), using filenames I found the position where the process stopped and the position of the old partition start. So, now I know the logical sector number of the first file, where the old partition started. Is it possible to use this information (maybe in Testdisk?) to put the partition start back in the right position? The 20.0 GB already moved will not work (I can copy them in the actual situation), but the others?

---

### Post by dragonfly41 on 2019-02-03
I recommend getting further advice on recovery of moved partition from [this forum]("https://forum.cgsecurity.org/phpBB3/") in addition to this Ubuntu forum.

[p.s.]

I searched that forum looking for pattern "moved" and [found this thread]("https://forum.cgsecurity.org/phpBB3/viewtopic.php?f=6&t=8320&p=26817&hilit=moved#p26817") which appears to be the OP.
That is the best source of advice.

---

### Post by fabma on 2019-02-03
Yes, I tried to have support also from software's author. But any advice from you here on Ubuntu Forum is welcome

---

### Post by dragonfly41 on 2019-02-03
I fear that we are in "last chance saloon" territory. Pointless pointing out that partition resize/move operations are risky if there is no backup.  You have learned this hard lesson.  There have been accounts of pets yanking out cables in mid-operation.

Now to alternative methods of recovery if Testdisk/Photorec fail.  But I would try the deeper search feature in these tools.

I would google search for off beat terms such as "recovering mangled partition" such as [this thread]("https://superuser.com/questions/929286/recovering-filesystem-in-mangled-partition").

There are recovery tools which just scan through the filesystem looking for file patterns.
Another point is that this partition is NTFS formatted so you can widen your horizon by looking at Windows recovery tools.
For example I have read good reviews about [SpinRite]("https://www.grc.com/spinrite.htm") but I have never used it myself. 

Another tool I have used is [R-Linux]("https://www.r-studio.com/free-linux-recovery/") which runs on Windows and Linux ([COLOR=#b22222]correction: R-Linux does not work on NTFS formats[/COLOR]).

The basic advice, before rolling up your sleeves, is to make a copy of the mangled drive to avoid losing any hidden data during recovery efforts.

[Later thought] Did you preserve the old configuration settings (partition table, sector size etc.) perhaps in a previous boot repair dump? This information might be useful in trying to reverse steps.

Also do not install fresh software such as recovery tools in the partition you are trying to recover since this might overwrite files you hope to recover.  Better now to remove and analyse the drive as an external drive in USB container connected to another fresh Ubuntu system.

==================================

[Further search] It seems that one approach is to try to change/restore the partition offsets .. [read here]("https://superuser.com/questions/275146/data-recovery-after-failed-partition-resize-move") .. and it would help if you can dig out old partition settings as I suggest from boot-repair dump or some settings you posted to a forum (admittedly a long shot). I don't know of any log which dumps this information and I now make a point of archiving partition settings from Gedit.

---

### Post by fabma on 2019-02-04
> **dragonfly41 said:**
> 
[Further search] It seems that one approach is to try to change/restore the partition offsets .. [read here]("https://superuser.com/questions/275146/data-recovery-after-failed-partition-resize-move")  .. and it would help if you can dig out old partition settings as I  suggest from boot-repair dump or some settings you posted to a forum  (admittedly a long shot). I don't know of any log which dumps this  information and I now make a point of archiving partition settings from  Gedit.

Thank you. I'm investigating exactly in this way, hoping to change the partition offset. At the same time I'm trying to check and reorder Photorec results. They are (long) audio files, and I don't know what could happen if the disk's fragmentation interrupts them. I don't know if the risk is "only" a truncated file or a file containing a piece of another file (for example if they have contiguous fragments). Anyway, I can compare file sizes. I also asked to software's creator.

> **dragonfly41 said:**
> 
[Later thought] Did you preserve the old configuration settings  (partition table, sector size etc.) perhaps in a previous boot repair  dump? This information might be useful in trying to reverse steps.
Unfortunately no :(

> **dragonfly41 said:**
> 
I would google search for off beat terms such as "recovering mangled partition" such as [this thread]("https://superuser.com/questions/929286/recovering-filesystem-in-mangled-partition").

There are recovery tools which just scan through the filesystem looking for file patterns.
Another point is that this partition is NTFS formatted so you can widen your horizon by looking at Windows recovery tools.
For example I have read good reviews about [SpinRite]("https://www.grc.com/spinrite.htm") but I have never used it myself. 

Another tool I have used is [R-Linux]("https://www.r-studio.com/free-linux-recovery/") which runs on Windows and Linux ([COLOR=#b22222]correction: R-Linux does not work on NTFS formats[/COLOR]).

Will fragmentation be a problem?

---

### Post by dragonfly41 on 2019-02-04
I can only suggest reading [this guide]("https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") again carefully.

In particular Partition Table Recovery.

I can't answer your question on fragmentation. You should not be de-fragging the mangled NTFS partition but trying to recover to its past state.  I think that defragging at this stage will throw a spanner in the works. 

Your google search should focus on "recover extended partition".

When you run testdisk take dumps of the screen to refer to later.

[P.S] There is a "guess" mode in Gedit to guess partition sizes.

---

### Post by dragonfly41 on 2019-02-05
Hunting for clues on partition sizes [COLOR=#b22222]*before and after extending*[/COLOR].

I found this approach to be useful.

First, install [ripgrep]("https://github.com/BurntSushi/ripgrep").

Now launch terminal and run commands ..

```
cd /var/log/
rg -i /dev/sda

```

Look through results for coloured patterns  [COLOR=#ff0000]/dev/sda[/COLOR]

I found that /var/log/boot-repair held useful data but unfortunately if you have never used boot-repair you will not see these logs.

However I see that parted (GParted) dumps information so there might be a dump [COLOR=#b22222]*before*[/COLOR] you extended (mangled) the partition using GParted.

---

### Post by fabma on 2019-02-07
> **dragonfly41 said:**
> 
However I see that parted (GParted) dumps information so there might be a dump [COLOR=#b22222]*before*[/COLOR] you extended (mangled) the partition using GParted.
I was running live, are those information stored on the disk?


> **dragonfly41 said:**
> 

I found that /var/log/boot-repair held useful data but unfortunately if you have never used boot-repair you will not see these logs.
No, I never used it :(

> **dragonfly41 said:**
> Hunting for clues on partition sizes [COLOR=#b22222]*before and after extending*[/COLOR].

I found this approach to be useful.

First, install [ripgrep]("https://github.com/BurntSushi/ripgrep").

Now launch terminal and run commands ..

```
cd /var/log/
rg -i /dev/sda

```

Look through results for coloured patterns  [COLOR=#ff0000]/dev/sda[/COLOR]


Ok, I will try ripgrep, thank you!

---

