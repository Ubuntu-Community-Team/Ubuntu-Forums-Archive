---
title: "How can I move root partition?"
date: 2006-11-10
forum: General Help
---

### Post by MblKiTA on 2006-11-10
I've got my hdd partitioned like this:

```

/dev/hda1 ntfs (Windows) (~ 20 GB)
/dev/hda2 ext3 (empty) (~ 90)
/dev/hda5 ext3 (Ubuntu) (~ 10 GB)

```

Can I move my root partition of Ubuntu from hda5 to make my hdd to be partitioned like this:

```

/dev/hda1 ntfs (Windows) (~ 20 GB)
/dev/hda2 ext3 (Ubuntu) (~ 10)
/dev/hda5 ext3 (empty) (~ 90 GB)

```

---

### Post by gborzi on 2006-11-10
I don't think you can. A brief explanation of why: on IDE disks you can have at most 4 partitions (hda1-4). To circumvent this problem extended partitions were introduced. These extended partitions are actually primary partitions that contains one or more partitions inside, which are called logical partitions. Due to the 4 partitions limit, the partitions inside the extended one are numbered starting from 5 (hda5-n with n >= 5). Actually you have a primary partition (hda1) with and extended partition (hda2) containing a logical partition (hda5). So you can't put Ubuntu (or any other OS) on your hda2 partition, because it is only a container for (logical) partitions.
I hope it was clear enough.

---

### Post by MblKiTA on 2006-11-10
oops sorry...
its not /dev/hda5 it's /dev/hda4 and it's not extended one...
gpart shows it as usual partition...

---

### Post by gborzi on 2006-11-10
Sorry, I don't know how to move partitions. I can only suggest to install Ubuntu on hda2 and remove it from hda4.

---

### Post by koenn on 2006-11-10
run a linux Live CD such as Dapper Drake Live and use Gnome Partition Editor to move / shrink / create partitions. 
Make a backup of your data first. 

You can't do this from your normal system because that is on one of the partitions you want to move/change and the partition is mounted.

---

