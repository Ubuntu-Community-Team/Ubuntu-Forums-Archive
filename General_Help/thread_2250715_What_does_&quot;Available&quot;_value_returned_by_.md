---
title: "What does &quot;Available&quot; value returned by the du command really mean?"
date: 2014-10-30
forum: General Help
---

### Post by sim085 on 2014-10-30
Hello,

When I enter the df -h command I get the following:

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       367G   67M  348G   1% /media/backup

```

However if you subtract 367GB by 67M the result should be 366.93GB and not 348GB. Why is Avail so low?
Also from fdisk /dev/sda is reported as a 400GB drive. This has one partition /dev/sda1 ... so where are the remaining 33GB (400GB-367GB)? I know that drives usually are smaller than what is reported on the label but 33GB seems a lot.

---

### Post by Impavidus on 2014-10-30
Part of the file system (by default 5%) is reserved for the root user and therefore not available. The reason for this is that in case thing go wrong because you have a full disk, you still have some headroom as root user to login (recovery mode in Ubuntu) and run some programs to solve the issue. For a backup partition this isn't very useful. It's possible to modify this amount of reserved space, using the tune2fs command. It must be mentioned in the forums somewhere.

A drive of 400GB has a size of 400GB=400,000,000,000 bytes. What df -h reports as 367G is 367GiB=394E9 bytes. Gigabinarybytes (GiB) are a unit that comes in an ugly mixed base-10/base-1024 system, being equal to 1024×1024×1024 bytes, but it is rather convenient when amounts come in powers of 2 – which hard disk space doesn't. But it is quite close to 400GB.

---

### Post by SeijiSensei on 2014-10-31
You can set the percentage when formatting a partition for an ext[234] filesystem, too.

```
sudo mkfs -t ext4 -m 1 /dev/sdc7
```

would create an ext4 filesystem with the reserved percentage set to one. 

Here is the rationale for reserving space for the root user as described by "man mke2fs"

> 
-m _reserved-blocks-percentage_

Specify the percentage of the filesystem blocks reserved for the super-user.  This avoids fragmentation, and allows root-owned daemons, such as syslogd(8), to continue to function  correctly after non-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.

On modern disks with hundreds of gigabytes available, the five percent default is much too high.  On a 1 TB drive, 5% is 5 GB.  There's no way syslogd and friends would ever come close to that.  A default that made sense in the 1990s, [when cutting-edge drives were a gigabyte in size]("http://en.wikipedia.org/wiki/File:Hard_drive_capacity_over_time.png"), doesn't make sense today.

---

