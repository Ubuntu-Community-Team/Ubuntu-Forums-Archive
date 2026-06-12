---
title: "Names of mounted volumes not showing up."
date: 2008-06-10
forum: General Help
---

### Post by billdotson on 2008-06-10
I have installed Hardy and have my XP, Vista and storage partitions in the fstab by UUIDs.  The mount points are names for the partitions I chose by creating /media mount points (through the use of the Hardy installer).  The mounted partitions are visible on the desktop but the names are only displayed for the Vista partition; the rest just say ex: 32.3 GB volume.

Thank you.

---

### Post by drs305 on 2008-06-10
You can use either of the following commands to label your partitions. I believe you have to reboot and not just remount to get them to be displayed. Of course, make sure the partition name is correct.

```
sudo tune2fs -L name /dev/sdaX 
```

or (for ext2 or ext3 partitions only):
```
sudo e2label /dev/**sdaX name**
```

---

### Post by billdotson on 2008-06-11
I tried both of those commands and got this output:

bill@Bill:~$ sudo e2label /dev/sda1 XP
[sudo] password for bill: 
e2label: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
bill@Bill:~$ sudo tune2fs /dev/sda1 XP
tune2fs 1.40.8 (13-Mar-2008)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
	[-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
	[-M last_mounted_dir] [-O [^]feature[,...]]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID] device


Thanks.

---

### Post by drs305 on 2008-06-11
> **billdotson said:**
> I tried both of those commands and got this output:

bill@Bill:~$ sudo e2label XP /dev/sda1
[sudo] password for bill: 
e2label: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
bill@Bill:~$ sudo tune2fs /dev/sda1 XP
tune2fs 1.40.8 (13-Mar-2008)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
	[-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
	[-M last_mounted_dir] [-O [^]feature[,...]]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID] device


Thanks.


In the second example, you omitted the "** -L **" which tells tune2fs to label /dev/sda1 to XP.
```
sudo tune2fsl **-L** XP /dev/sda1
```

The reason you got all the info was that tune2fs was asking you what you wanted to do and gave you the options available.

I didn't relate which partitions you were trying to label. e2label will only work on ext/ext3 partitions. I will go back and annotate that in my previous post.

---

### Post by DJ_Peng on 2008-06-12
> **drs305 said:**
> You can use either of the following commands to label your partitions. I believe you have to reboot and not just remount to get them to be displayed. Of course, make sure the partition name is correct.

```
sudo tune2fs -L /dev/**sdaX name**
```or (for ext2 or ext3 partitions only):
```
sudo e2label /dev/**sdaX name**
```
Thanks for this! It finally resolved my issue of missing partition labels.

---

### Post by billdotson on 2008-06-12
Hmm, well my Vista partition name is showing up but XP is not.  I need the names to show up for all of my partitions, not just ext2/ext3.  This worked fine in Gutsy...

---

### Post by drs305 on 2008-06-13
> **billdotson said:**
> Hmm, well my Vista partition name is showing up but XP is not.  

I don't really understand why one NTFS partition would successfully be labeled but another one not. Here is an alternative method of labeling it:

Install ntfsprogs:
```
sudo apt-get install ntfsprogs
```

After the drive is automounted after plugging in, find out the device descriptor using and note the designation (sdaX, etc):
```
mount
```

Change the label:
```
sudo ntfslabel /dev/sda1 newlabel
```

You may have to unmount the drive for this to work (system-> administration-> disks -> then under partitions for the hard disk hit disable). 

Reboot to see the results.

This method comes from the ubuntu documentation pages.

---

### Post by billdotson on 2008-06-27
Hmm, I will try that.  I wonder why this hasn't just been working from the beginning.  I have never had any problems with this sort of thing before Hardy.

---

### Post by mmoalem on 2008-07-07
hi there - having the same problem - this is the output...
> michel@michel-laptop:~$ sudo tune2fs -L /dev/sda1 sda1
[sudo] password for michel: 
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: No such file or directory while trying to open sda1
Couldn't find valid filesystem superblock.
michel@michel-laptop:~$ sudo tune2fs -L /dev/sda3 sda3
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: No such file or directory while trying to open sda3
Couldn't find valid filesystem superblock.
michel@michel-laptop:~$ sudo tune2fs -L /dev/sda6 sda6
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: No such file or directory while trying to open sda6
Couldn't find valid filesystem superblock.
michel@michel-laptop:~$ 


partitions: sda1-ntfs(xp) sda3-ext3 sda6-fat32


what next?

---

### Post by drs305 on 2008-07-07
> **mmoalem said:**
> hi there - having the same problem - this is the output...


partitions: sda1-ntfs(xp) sda3-ext3 sda6-fat32


what next?

run tune2fs on ext2 or ext3 as:
```
tune2fs -L *name* /dev/sdXX
```

the syntax is different than e2label or ntfslablel. I've corrected my previous posts.

---

### Post by mmoalem on 2008-07-09
hi there and thanks for the help
i managed to change the label on the ntfs and ext3 partitions but still get the same reply of "bad magic number in super block" when trying to label the fat32 partitions

any ideas?

---

### Post by drs305 on 2008-07-09
> **mmoalem said:**
> hi there and thanks for the help
i managed to change the label on the ntfs and ext3 partitions but still get the same reply of "bad magic number in super block" when trying to label the fat32 partitions

any ideas?

Here is a link to a post by bodhi.zazen. Even though it is primarily about fstab, there is a section on how to label partitions. Look about 1/4 of the way down the post. It's not a simple thing to label a fat partition but he instructs you how to do it.

Here is the link:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Vivaldi Gloria on 2008-07-10
> **billdotson said:**
> ...  The mount points are names for the partitions I chose by creating /media mount points (through the use of the Hardy installer).  The mounted partitions are visible on the desktop but the names are only displayed for the Vista partition; the rest just say ex: 32.3 GB volume.


Linux Filesystem Hierarchy Standard stipulates that

> This (/media) directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks.

It is customary to mount hard disks to

```
/mnt/mountpoint
```

via fstab. Then disks don't show icons on the desktop and you can put a symlink from /mnt/mountpoint to where ever you want and name it whatever you want.

Trying to label the disk (e.g. C:, D:, John, Whatever) and using those is indicative of a windows mindset. I suggest you do it the linux way. ;)

---

### Post by billdotson on 2008-07-10
I tried doing tune2fs and ntfslabel and it didn't work for either.  The only partition that has the correct name on the desktop is Vista.  The rest jsut show up as ?? GB Volume (?? being the size).  This is confusing.

---

### Post by mmoalem on 2008-07-11
hi there again and thanks for the advice had a quick look at the post and it seems a bit complicated - will need to get my head around it before i start changing the fstab...
what i dont understand is how come this was not a problem in gutsy. all partitions came out named correctly after install and so any pluged in usb card. why has ubuntu went a step back?

---

