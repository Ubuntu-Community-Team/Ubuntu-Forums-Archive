---
title: "Backup files from one partition to another"
date: 2008-03-25
forum: General Help
---

### Post by DrObviousSo on 2008-03-25
I have a NTFS partition on one hard disk, and another, much larger NTFS partition on another disk.  I'm considering setting up a RAID system, but if I don't end up doing that, I was thinking about making an image of the smaller partition, and putting a copy of that on the larger partition at a regular interval (say once a week or so)

Can anyone point me in the direction of the tools I'll need to do that?  I guess it doesn't have to be a disk image, I could just copy over all the files.  I don't know which will be easier.

---

### Post by kpkeerthi on 2008-03-25
I suggest you use 'tar' for backup if you need to have the backup process run transparently behind the scenes (using a cron) without manual intervention. 

If you use 'image' backup ([partimage]("http://www.sysresccd.org/"), [clonezilla]("http://clonezilla.sourceforge.net/")), you should be in a Live CD, kind of intrusive for me. 

See [this]("http://linuxmint.com/forum/viewtopic.php?f=42&t=3969") for an excellent howto

---

### Post by cmnorton on 2008-03-25
Mine is not a smart question, but I'll ask it anyway. If you have two NTFS partitions, why are you doing this from the Linux and not Windows side? You have to have NTFS, FAT16, or FAT32 on Windows, but not on Linux.

Are you interested in backing up the partition or duplicating the partition?

Is the larger NFTS partition to be in active use by users, or do you have the partition strictly as a repository for the first partition?

Assuming both partitions are actively in use, I would use a combination of tar and gzip. That is I would tar at the top of the partition; pipe it into gzip; and have gzip create the file in the second partition.

dd is the true Linux/Unix copy tool. It will handle this task at the device level, below the file system level, and it is not sophisticated. It will back up unused disk space as well as well that which has been written to. However, to the best of my knowledge, you have to have no activity on either the source or destination volumes. You can ensure this by booting into init level 1.

There are commercial and open source products. Acronis is an excellent Linux tool, but is pricey (around $700.00). I believe there is an open source product called Partimage. I've never used it. Usually, I make a skeleton backup of my installation using dd and booting from Knoppix. Then, I backup my data.

---

### Post by DrObviousSo on 2008-03-25
kpkeerthi -> Thanks, that looks like what I'm looking for.

cmnorton -> I have to dual boot pretty regularly between XP and ubuntu.  XP for work, ubuntu for everything else.  This data needs to be read/write from both OS's, and the NTFS partition predates my migration to ubuntu.  I want to schedule this for the middle of the night, and the computer will be running ubuntu at the time.

---

### Post by cdenley on 2008-03-25
```

sudo apt-get install ntfsprogs
man ntfsclone

```

---

### Post by DrObviousSo on 2008-03-25
Thanks cdenley, that may also look very useful.

---

