---
title: "Corrupted ext4 partition - advice how to recover?"
date: 2020-05-31
forum: General Help
---

### Post by cghall74 on 2020-05-31
I am the main linux person in our team (which is a sad state of affairs), and am trying to fix a problem created by one of our windows users. I have searched many forums but haven't found quite this exact issue.

They had a 5TB drive with a single ~5TB ext4 partition with a bunch of video files. They weren't the one who set up the drive, so when they couldn't access it in windows they went into disk manager and " converted to GPT" in windows disk manager. Now it isn't accessible in ubuntu either.

[LIST]
[*]Disk: Seagate ST5000DM
[*]fdisk reports: the wrong disk size
```
Disk /dev/sdg: 561.5 GiB, 602934566912 bytes, 1177606576 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disklabel type: dos Disk identifier: 0xa6985519
```
[*]Testdisk reports the wrong disk size: ```
Disk /dev/sdg - 602 GB / 561 GiB - ST5000DM 000-1FK178
```
[*]fsck reports:
```
fsck from util-linux 2.31.1 e2fsck 1.44.1 (24-Mar-2018) ext2fs_open2: Bad magic number in super-block fsck.ext2: Superblock invalid, trying backup blocks... fsck.ext2: Bad magic number in super-block while trying to open /dev/sdg
The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem. If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 or e2fsck -b 32768
Found a PMBR partition table in /dev/sdg
```
[*]Gdisk reports: ```
Caution: The CRC for the backup partition table is invalid. This table may be corrupt. This program will automatically create a new backup partition table when you save your partitions.
Problem: The secondary header's self-pointer indicates that it doesn't reside at the end of the disk. If you've added a disk to a RAID array, use the 'e' option on the experts' menu to adjust the secondary header's and partition table's locations.
Problem: Disk is too small to hold all the data! (Disk size is 1177606576 sectors, needs to be 9767541168 sectors.) The 'e' option on the experts' menu may fix this problem.
Problem: GPT claims the disk is larger than it is! (Claimed last usable sector is 9767541134, but backup header is at 9767541167 and disk size is 1177606576 sectors. The 'e' option on the experts' menu will probably fix this problem
Problem: partition 1 is too big for the disk.
Partition(s) in the protective MBR are too big for the disk! Creating a fresh protective or hybrid MBR is recommended.
Identified 6 problems!
```[/LIST]
File recovery programs can still read the files, so I can fall back on that if I have to, but it will take forever and lead to endless sorting and renaming of files. I am hoping I can " fix" the partition table to be able to mount the drive and immediately back up the data onto a secure, backed up location.
Thanks for any assistance. Any guidance on what to try is appreciated. I haven't had to deal with this kind of thing before, my linux usage is pretty vanilla.

---

### Post by guiverc on 2020-06-01
Just FYI:   Asked earlier on [https://askubuntu.com/questions/1245380/corrupted-ext4-disk-with-windows-disk-manager](https://askubuntu.com/questions/1245380/corrupted-ext4-disk-with-windows-disk-manager)  (*no responses at this point in time*)

---

### Post by DuckHook on 2020-06-01
Thanks for the heads'&#8209;up guiverc.

@cghall74

Welcome to the forums.

It is permissible to post on both UF and our sister site. However, it is considered only good netiquette to then respond on each site.

Re: your problem:

So, this "Windows user" did not have proper backups either? ](*,) In a fair world, you would make him/her go recover those files one by one.

The first thing to do is to not touch the corrupted drive except to make a bit&#8209;for&#8209;bit copy. Instructions: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As per above link, if ```
dd
``` is deemed too difficult, then ```
gddrescue
``` will slap a GUI onto it that makes the copying exercise a bit more user friendly. Once copied, work on the copy of the original, never the original itself.

Unfortunately, there's no further magic answer after this. You are obviously familiar with Testdisk. It has a partition recovery function that you can try. The instructions are in Chapter 9 of the Testdisk Users' Manual: [https://www.cgsecurity.org/testdisk.pdf](https://www.cgsecurity.org/testdisk.pdf)

Best of Luck. If you succeed, that "Windows user" owes you donuts for a year.

---

### Post by cghall74 on 2020-06-01
Sorry I didn't realize the two forums were linked, my apologies.

As to the disk, not much luck recreating the partition table, but the most critical info it looks like we have on an LTO, it is just a pain to get the tape back from Iron Mountain. Photorec is also pulling a lot of files as well so hopefully the things that weren't on the backup we can recover if they are willing to sift through the files.

As a silver lining, perhaps they will refrain from using passing around a USB drive as a viable form of reliable data transfer. We keep telling them that the Gigabit network would be faster anyways.

Thanks for the feedback, have a great week.

---

### Post by oldfred on 2020-06-01
If a 5TB drive, it had to be gpt partitioned.
So then did your user convert to MBR which would then limit drive to 2TB and rest hidden or lost.

After good backup, I would use gdisk to convert/repair gpt structure. Not sure if order of fixes is important.
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

---

### Post by TheFu on 2020-06-01
I'm lazy.  I'd get the tapes from Iron Mountain.  After all, what's the point if you don't use them?  Let the user's group pay for any extra cost involved. If you can, bill your time to their charge account too.

Do no harm is the first rule of data recovery. Use ddrescue to make a clone.  Think gddrescue is the GNU version, not a GUI. [https://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue](https://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue)

Anywhere I would normally use dd, I use gddrescue (package name) which installs ddrescue (program).
After the clone is done, don't touch the original disk again until after
a) all the data is restored
b) the restore effort has ended (people gave up)

This is a great opportunity to get the restore process nailed down for other systems too.  People make backups all the time, but never validate the restore process works.

---

### Post by cghall74 on 2020-06-01
Thanks all.

I wasn't able to recover the partition, but was able to use Photorec to recover the files that weren't on tape. My only regret is not being able to scold them in person due to the covid19 distancing.  :D 

I appreciate the effort everyone puts out on these forums, I am not sure my level of expertise is at a helpful level among this group, but I will try.

---

### Post by DuckHook on 2020-06-01
At least it's good to know that the final result was not complete disaster. When it comes to HDD problems, small victories are still victories.

And don't sell yourself short. Your first post already demonstrated system&#8209;level knowledge including familiarity with as specialized an app as Testdisk. I started out on these forums with far less knowledge.

I think you will find that a person with your expertise is very valued and welcome here.

Cheers!

---

