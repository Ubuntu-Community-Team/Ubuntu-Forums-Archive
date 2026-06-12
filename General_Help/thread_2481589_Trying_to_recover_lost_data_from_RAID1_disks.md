---
title: "Trying to recover lost data from RAID1 disks"
date: 2022-12-03
forum: General Help
---

### Post by deep7861 on 2022-12-03
I'm trying to locate/recover data on my RAID1 setup with 2 4TB HDDs. Have been using a bootable NAS OS (Debian based) off from a USB stick, so, these data disks are not bootable. Running 'testdisk' on /dev/md0, it doesn't find the files to undelete:
first it detects None partition (which I think may be right since there were only folders created on the RAID, no partitions as such - but even then, should find one major partition, I'd believe). If I went further and said analyze, it shows one EXT4 partition with quick search option. The advanced option which I think gives option to undelete isn't showing anything except partition and 'type, superblock, list, image creation, quit' options:

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/md0 - 4000 GB / 3725 GiB - CHS 976721616 2 4

     Partition                  Start        End    Size in sectors
>   P ext4                     0   0  1 976721615   1  4 7813772928



>[  Type  ]  [Superblock]  [  List  ]  [Image Creation]  [  Quit  ]
              Change type, this setting will not be saved on disk
```

The disk is getting mounted but doesn't show anything except used/free data:

```
root@signtrigger-nas-prod:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.1M  1.6G   1% /run
/dev/sdc1        14G  2.2G   11G  17% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G     0  7.8G   0% /tmp
/dev/md0        3.6T  2.2T  1.5T  61% /srv/dev-disk-by-id-md-name-signtrigger-nas-prod-0
```

Any suggestions on if I could recover the data and how?
I have two 4TB HDDs running in software RAID1 configuration for storing data. I've been booting an open source NAS OS (Debian based) from a USB stick. This is an old setup with everything running smoothly past couple of years but I accidentally tried to re-write file system on the RAID disk /dev/md0. The moment this mistake was realized, I stopped the process in between by forcing power off. As it was supposed to happen, the data is inaccessible now. I tried to fix RAID sync by running:```
mdadm --readwrite /dev/md0
```…which did the job (made RAID in sync), but nothing to fix the damage. Second thing I did after that was:```
fsck /dev/md0
```…which claimed to fix something but data is yet not visible. ```
mke2fs -n /dev/md0
```…is giving following output:

```
root@signtrigger-nas-prod:/# mke2fs -n /dev/md0
mke2fs 1.43.4 (31-Jan-2017)
Creating filesystem with 976721616 4k blocks and 244187136 inodes
Filesystem UUID: 937674a5-c04c-496e-828b-f8b737aa37a2
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544
```

I tried this for few superblocks:```
fsck.ext4 -p -b 32748 -B 4096 /dev/md0
```…but doesn't help (guess it wasn't the problem)

Any help on this would be really appreciated.

---

### Post by TheFu on 2022-12-03
If you don't have backups, I don't think you'll get the files back, without replacing the bad disk and giving the OS 24 hrs to resync the data.  You can try to run the RAID1 setup in a degraded mode and mount it.  The mdadm manpage explains how to do that.  You'll want to use the --detail and examine options to gather information about the RAID first.  Each SW-RAID that I setup, I retain the exact commands used to create it, so later when I need to replace a failing drive, I have those details.

If both drives failed, you are screwed.  First step is to tell the RAID to fail the broken partition. Something like:
$ sudo mdadm --manage /dev/md1  --fail /dev/sde2
Then remote that partition from the RAID set:
$ sudo mdadm --manage /dev/md1  --remove  /dev/sde2
Swap the failed drive for a new drive (or if you have hot-swap) or shutdown the system and replace the failed disk for the new one.
I clone the partition table from the good/working drive next, 
$ sudo sgdisk -R    /dev/sdc   /dev/sdd  # sdd is the source and sdc is the target - yes, the is backwards of what is expected.
$ Force the GUIDs to be changed on teh new drive/partitions:
$ sudo sgdisk -G /dev/sdc
Add the new partition to the RAID:
$ sudo mdadm --manage /dev/md1 --add /dev/sdc3
This will start the data sync process. You should watch the progress in 
the /proc/mdstat file.

With software RAID, it is a good idea to check and repair it monthly. I do it with a monthly cron job.

BTW, Debian isn't Ubuntu. Wrong sub-forum for this post. I don't know that Debian has any differences in mdam than Ubuntu, but that doesn't matter. The Debian-based subforum would be more correct.  A moderator will probably move this thread there.

Many data recovery tools only work if there are partitions, which is 1 reason why the best practice for using RAID is to always, always, always, setup partitions for the RAID areas, never use the whole drive.  It also makes replacing failed drives with different models of drives possible since they are all built with slightly different sizes.  OTOH, by using partitions for the RAID storage, we can set the exact size to match regardless of the drive model or make.  Hard to do that without any partitions.  Live and learn.

RAID doesn't replace backups.  Just restore the files from your backups.  RAID solves 2 issues (HA and some performance improvements), backups solve 1001 issues, including RAID corruption.  If the issue is data corruption caused by a bad controller or bad application software, RAID doesn't help.  You'll need versioned backups.

As a run, backups are 1000x more important than RAID-anything. Don't do RAID until you have excellent backups that you KNOW can be restored first.  If it isn't important enough to have backups, then it definitely isn't important enough to be RAID.

---

### Post by SeijiSensei on 2022-12-04
I've had a couple of RAID1 arrays that I created using mdadm. In both cases I could mount one of the disks as ext4. Try booting from an Ubuntu USB image (choose "Try Ubuntu") and see if you can mount either device as an ordinary ext4 filesystem.

---

### Post by deep7861 on 2022-12-14
Hi, Thanks both for responding. I have been caught up in past few days and so was unable to respond here. 
The disk hasn't gone bad actually - rather, I happened to re-write file system on the array and that's where things went wrong. 

Array itself is getting mounted and it's showing the used vs available capacity which was right when data was present - but directory is all empty. 
/dev/md0        3.6T  2.2T  1.5T  61% /srv/dev-disk-by-id-md-name-signtrigger-nas-prod-0

---

