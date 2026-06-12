---
title: "Trouble with dd_Rescue and FSCK w/ NTFS Drive"
date: 2007-12-28
forum: General Help
---

### Post by datapusher on 2007-12-28
Hi all, Trying to do some data recovery on my mother's NTFS XP drive.

I had her **80G **drive set up so that it had:
C: System
D: Music
E: Documents
F: Backups

Well for some reason it stopped booting and it is showing only one partition.  The system partition.  however, it shows the system partition as using the entire disk.  however, as described above, the system partition does not take up the entire disk.  Also, this drive will not mount when plugged into another XP computer.  You can however see the drive and partition under the drive manager toolset.

Well, I was able to mount the main partition under ubuntu and grab her emails and favorites and desktop.  For that I am grateful.

However, I am really trying to salvage her Documents partition.

So I have doing the following:

Moved to a NTFS partition on another drive with plenty of space to hold my Mothers dd_rescue image.
```
**cd /media/FREESPACE/**
```

Just to be sure
```
**pwd**
```

Ran dd_rescue on the drive in question.  I didn't specify any partitions, just the whole drive.  not sure if that is correct or not.  it did return me an ~80gb image file.
```
**sudo dd_rescue /dev/sdb disk.img**
```

I decide to take a little nap while thgis completes.  i wake up to the following: 
```

[I]dd_rescue: (info):  ipos:  78124992.0k, opos:         78124992.0k, xferd:  78124992.0k
                    errs:      0, errxfer:                0.0k, succxfer:  78124992.0k
              +curr.rate:    30938kB/s, avg.rate:    42878kB/s, avg.load:  7.4%
dd_rescue: (info): /dev/sdb (78125000.0k): EOF
Summary for /dev/sdb -> disk.img:
dd_rescue: (info): ipos:  78125000.0k, opos:         78125000.0k, xferd:  78125000.0k
                   errs:      0, errxfer:                0.0k, succxfer:  78125000.0k
             +curr.rate:    37037kB/s, avg.rate:    42878kB/s, avg.load:  7.4%[/I]

```

So according to the posts I have read, I do the following:
```
**sudo fsck -y /media/FREESPACE/disk.img**
```

But this throws out the following errors:
```
[I]fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /media/FREESPACE/disk.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>[/I]
```

OK, I need to tell it the img file in question is NTFS.  OK, I'll read the Man pages.  Well after reading the man pages I try the following:

```
**sudo fsck -yA /media/FREESPACE/disk.img**
[I]fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=BADC-8F02:No such file or directory[/I]
```

```
**sudo fsck -y -A /media/FREESPACE/disk.img**
[I]fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=BADC-8F02:No such file or directory[/I]
```

```
**sudo fsck -t ntfs -y /media/FREESPACE/disk.img**
[I]fsck 1.40.2 (12-Jul-2007)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /media/FREESPACE/disk.img[/I]
```

So I am not really sure what to do now.  I need to tell fsck that the image file in question is NTFS correct?  Did I do anything wrong?  What is my next step here as far as getting this image to check, repair and mount itselfso I can snag her data off?

Thank you for your time.

---

### Post by frego on 2007-12-28
You're on the right track..but fsck won't do what you're trying there. 

Now that you have the .img of the file using ddrescue, put the bad drive on a shelf and leave it be and play with the image.  I did notice there were zero errors according to the text you posted. Maybe this drive isn't bad?  Anyways, you can mount it using: 

sudo mkdir /mnt/recovered
sudo mount -t ntfs-3g -o force,loop /media/FREESPACE/disk.img /mnt/recovered

Now, by browsing over to /mnt/recovered, you can start to copy the data you want off it.  

FSCK wasn't working to repair your image (as it would if it were ext2/3 as it doesn't have ntfs support for that yet as far as I know.  So to do what you are attempting, you would need to grab a drive the same capacity or larger and dd the .img contents to this new drive.  Then, boot into a windows system and chkdsk it.

---

### Post by nisarg on 2008-03-12
Hi,

I am wondering if you can give me a hand with ddrescue.
Heres, the thread I started. 
[http://ubuntuforums.org/showthread.php?t=722350](http://ubuntuforums.org/showthread.php?t=722350)

I need to resume the backup that was running for over a week, and crashed due to may be a reset or something on the network.
Now when I am using the same command I used previously, pointing to the same backup.img and backup.log it starts and then terminates in a couple of mins with error: Invalid argument.
Would you be able to help?
Thanks, N

---

