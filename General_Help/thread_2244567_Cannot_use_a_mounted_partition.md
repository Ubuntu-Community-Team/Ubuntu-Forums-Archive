---
title: "Cannot use a mounted partition"
date: 2014-09-17
forum: General Help
---

### Post by charitosha on 2014-09-17
Recently, i decided to merge my biggest partition (sda1), which had windows in it, with linux.
Heres is the thread that i made to find help with that matter: [http://ubuntuforums.org/showthread.php?t=2241589&page=2](http://ubuntuforums.org/showthread.php?t=2241589&page=2)

However, there seems to be somethings wrong... Among other things, the biggest issue is that the sda1 partition cannot be used.
I cannot create folders/files in it and also i cannot paste files in it.

If anyone can help me, and needs some more info, please ask.

---

### Post by TheFu on 2014-09-17
```
**sudo parted -l**
**df -h**
**more /etc/fstab**

```
Please.

---

### Post by yancek on 2014-09-17
I'm not sure what you were planning but what you did is overwrite your windows and formatted the partition (sda1) as a separate /home partition for Linux.  Check the permissions on it which are probably wrong by opening a terminal and running this command:  ls -ld /home
You can post that output here for an explanation or possible suggestions.

---

### Post by charitosha on 2014-09-17
```
~$ ls -ld /home
drwxr-xr-x 4 root root 4096 Jan 12  2014 /home

```

```

~$ sudo parted -l

Model: ATA Hitachi HTS72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  205GB  205GB   primary   ext4
 3      205GB   250GB  45.1GB  extended
 5      205GB   248GB  43.0GB  logical   ext4
 6      248GB   250GB  2133MB  logical   linux-swap(v1)

```

```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        40G  6.5G   31G  18% /
udev            994M  4.0K  994M   1% /dev
tmpfs           201M  896K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M   84K 1001M   1% /run/shm
/dev/sda1       188G  2.8G  176G   2% /home

```
(out of curiosity, what are those "none" filesystems mmentioned in df -h?)

```

more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=934cb3ca-9bb8-4fe5-b9fb-91776b0b6619 /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46 none            swap    sw            
  0       0
UUID=c77cb893-a53b-423a-a0a5-a6b402d861bb /home  ext4  defaults 0 2

```

---

### Post by TheFu on 2014-09-17
/home is mounted and the permissions seem correct. So far, so good.

```
ls -ld /home/*
```

---

### Post by Impavidus on 2014-09-17
You say you can't write to your /home partition? In that case I wonder how you succeed in logging in to the GUI.

What exacly goes wrong and what did you try?

---

### Post by charitosha on 2014-09-17
I did mount the partition successfully, but there is always a chance that i missed something and thus i've got those problems...
For example besides the fact that i cannot create, delete and paste folders and/or files in sda1, another issue is that while sda5 was working flawlessly now i cannot access any of it's folders, because i get permission denied. Have to use nautilus.

```
ls -ld /home/*
drwxr-xr-x 38 haris haris  4096 Sep 17 14:54 /home/haris
drwx------  2 root  root  16384 Sep  5 22:17 /home/lost+found

```

Any ideas? (or some more infos?)

---

### Post by ajgreeny on 2014-09-17
> **charitosha said:**
> I did mount the partition successfully, but there is always a chance that i missed something and thus i've got those problems...
For example besides the fact that i cannot create, delete and paste folders and/or files in sda1, another issue is that while sda5 was working flawlessly now i cannot access any of it's folders, because i get permission denied. Have to use nautilus.

```
ls -ld /home/*
drwxr-xr-x 38 haris haris  4096 Sep 17 14:54 /home/haris
drwx------  2 root  root  16384 Sep  5 22:17 /home/lost+found

```

Any ideas? (or some more infos?)
What do you mean by "now i cannot access any of it's folders, because i get permission denied. Have to use nautilus."?

If you can use nautilus to access the folders then surely it means that *you can access* them.  Have I misunderstood what you mean?

Just to check your fstab syntax properly, please can we see the output of ```
sudo blkid -c /dev/null
```

---

### Post by TheFu on 2014-09-17
Uh .... seems like a better understanding of users, groups, directory and file permissions is needed. 
I don't see anything wrong, provided you are logging in as "haris".

Linux is multi-user. Different userids have different permissions to different parts of the file system. THAT is the core for security in the OS.  Am I missing something?

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a free, non-hassle, download PDF book that will provide an organized introduction and explanation.

---

