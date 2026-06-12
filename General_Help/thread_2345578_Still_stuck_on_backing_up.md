---
title: "Still stuck on backing up"
date: 2016-12-05
forum: General Help
---

### Post by Gnusboy on 2016-12-05
I am still stuck on trying to backup my system to do a clean install of 16.04
I've tried everything I can find to copy the important stuff, but nothing seems to work.
I keep getting "disk full" error, but I have gigs and gigs available on my internal drive and the external drive.

"Error while creating directory Untitled Folder.
There was an error creating the directory in /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1.
Error creating directory: No space left on device"

I have tried every fix offered here as well as, Grsync, Deja Dup, and Clonezilla. None of these work for me.
I had hopes for Grsync, but the only manual I found was far out of date and its instructions did not relate to the data or images I saw.

At this point I'm ready to slick all my drives and start from absolute scratch. I must get my system working properly and save important backups.

I'm not whining, Though I've been using Ubuntu for a few years, I tend to learn only what is necessary for my needs. It is frustrating to spend hours and hours
looking for things I need and drowning in a sea of confusion. I just want to do what I need doing. If I can get some instruction written for a two year old child - maybe it will help.

All life ropes appreciated.
Thanks.

---

### Post by TheFu on 2016-12-06
Nothing will work until you determine which storage is out of space and what type of space it is lacking.

Start by posting the cmd and output from 2 commands:
```
df -ih
df -h
```
I suspect you are out of i-node space, but won't know for sure without the output from those commands. If the command won't run (out of space is a terrible thing), then boot off a flash drive and mount the internal and external storage, then run those commands.

The permissions issues, I assume you can handle (after running Linux for 2 yrs).

---

### Post by HermanAB on 2016-12-06
Yup.  If you have an underlying file system problem then nothing you try to do on top of that is going to work.

Since you want to do a clean install anyway, boot off your install disk (USB schtick or DVD), then mount the disks and do the backup using the tools on the install disk.

---

### Post by Gnusboy on 2016-12-08
Thanks guys
I assume that an empty partition would be fine for the clean install, yes?
Does a partition need to be mounted to do an install?
And, will the fix solve my backup problems across the system in other partitions? My thought is that if I have a 500 GB partition about 15 % full, can I move that data to a separate partition,
which leaves a completely empty partition ready for me to do the clean install of 16.04?
Can I do the transfer of data internally or do I need to copy it to some other device and then into an available partition?
  
This is the output from

df -ih  df -h
----------------------------------
ranhanrio@Ranha:~$ ^?
: command not found
ranhanrio@Ranha:~$ df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
udev             452K   546  452K    1% /dev
tmpfs            463K   572  463K    1% /run
/dev/sda8        6.6M  1.4M  5.3M   21% /
none             463K     2  463K    1% /sys/fs/cgroup
none             463K     3  463K    1% /run/lock
none             463K     7  463K    1% /run/shm
none             463K    28  463K    1% /run/user
/dev/sdb1        128K    11  128K    1% /media/ranhanrio/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3        108K  108K     0  100% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1
/dev/sdb2        125K  125K     0  100% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3
ranhanrio@Ranha:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           371M  1.2M  369M   1% /run
/dev/sda8       104G   25G   75G  25% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  156K  1.9G   1% /run/shm
none            100M   48K  100M   1% /run/user
/dev/sdb1       976M   60K  976M   1% /media/ranhanrio/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sdb3       431G   75G  356G  18% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1
/dev/sdb2       500G   78G  423G  16% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3
ranhanrio@Ranha:~$ ^C
ranhanrio@Ranha:~$ 

Comments?

---

### Post by TheFu on 2016-12-08
```

Filesystem Inodes IUsed IFree IUse% Mounted on
/dev/sdb3 108K 108K 0 100% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1
/dev/sdb2 125K 125K 0 100% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3
```

Full. Out of i-node space.  [https://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html](https://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html) explains i-nodes.  You'll need to fix that issue before any more data can be added to either of those file systems.  Being short on i-nodes sucks and is more of an issue on smaller disks due to the default settings. If lots and lots of tiny files are placed on a file system, then lots and lots and lots of i-nodes need to be planned for.

I don't know how to fix that short of wiping everything on that file system and recreating it with 50x more i-nodes pre-allocated using **mkfs** with the inode tuning parameter, -N.  Whatever the default number is, I'd make it 50x-100x higher.

It is a pain when this happens.  It has happened to me on a few servers with really small disk allocations (1G-4G) that run webapps. Wish I had a better answer.

Also, please use code tags so things line up.

---

