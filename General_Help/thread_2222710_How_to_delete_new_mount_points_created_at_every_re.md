---
title: "How to delete new mount points created at every reboot?"
date: 2014-05-07
forum: General Help
---

### Post by panczol on 2014-05-07
Every time I reboot, Kubuntu creates a new mount point under the /media/username directory. I've searched the forum but didn't find an answer.

How do I delete these mount points without deleting the files they point to?

That is, I have the following:

/media/hdd010 only contains directory username
/media/username 
/media/username/hdd0101 only contains directory username
/media/username/hdd0102 only contains directory username
/media/username/hdd0103 only contains directory username
/media/username/hdd0104 correctly contains the six directories I expect

I want to get rid of hdd0101-hdd0103.

Here is the perinent output of mount:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)

...

/dev/sdb1 on /media/username/hdd011 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc1 on /media/username/hdd0104 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

---

### Post by sandyd on 2014-05-07
Hi,
You can mount the partitions in fstab - then they will not be managed by kubuntu.

First, you will have to find the UUID.
You can do this by running
```

blkid
```

Then, you can unmount the partitions that you want.
```

sudo umount /dev/sdb1
sudo umount /dev/sdc1

```

Before continuing, make sure that you have unmounted all partitions that mount in /media/username
```

sudo mount -l
```

Remove the mount folders (rmdir does not delete non-empty folders)
```
sudo rmdir /media/username/*
```

Create mount points for the two partitions
```
mkdir /media/username/sdb1
mkdir /media/username/sdc1
```

Now, you can add the entries to fstab
```

sudo nano /etc/fstab
```

Add a new line at the bottom of the file for each partition in the format below, where XXXXXX is the UUID of your partition
```

UUID=XXXXXX  /media/username/sdb1  ext4  relatime,errors=remount-ro  0  0
UUID=XXXXXX  /media/username/sdc1  ext4  relatime,errors=remount-ro  0  0

```

When you are done, save by pressing Control+X, and pressing 'y' when asking if you want to save.

Then, we can test the remount.
```

sudo mount -a
```

Note that the above assumes that you have only ext4 partitions. For example, if your using XFS, youll need to change ext4 to xfs in the fstab file.

---

