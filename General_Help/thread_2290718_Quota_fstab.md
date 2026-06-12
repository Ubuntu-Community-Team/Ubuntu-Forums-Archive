---
title: "Quota fstab"
date: 2015-08-14
forum: General Help
---

### Post by snakyjake on 2015-08-14
I want to add a quota to /home.
What am I supposed to add/change to the fstab?
Why does my fstab look different?

This is the document I'm trying to follow:  [Quota HOWTO](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas)
I'm stuck on step "Edit Your /etc/fstab File".

My fstab looks like this:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0ab56e90-db11-4ada-9844-a2d56d570c30 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=9912-4FC8  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
#UUID=804db270-0a03-4cae-b978-4299fd62e130 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0

```

Do I simply add this line to the bottom?
Not sure what the "1" and "2" mean?
```
LABEL=/home     /home   ext4    defaults,grpquota,usrquota       1       2
```

Or am I supposed to change the UUID=0ab56e90-db11-4ada-9844-a2d56d570c30 line?

---

### Post by kerry_s on 2015-08-14
it appears you did not install with a separate /home

---

### Post by bab1 on 2015-08-14
> **snakyjake said:**
> I want to add a quota to /home.
What am I supposed to add/change to the fstab?
Why does my fstab look different?

This is the document I'm trying to follow:  [Quota HOWTO](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas)
I'm stuck on step "Edit Your /etc/fstab File".

My fstab looks like this:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
**[COLOR="#FF0000"]UUID=0ab56e90-db11-4ada-9844-a2d56d570c30      /            ext4    errors=remount-ro 0       1[/COLOR]**
# /boot/efi was on /dev/sda1 during installation
UUID=9912-4FC8  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
#UUID=804db270-0a03-4cae-b978-4299fd62e130 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0

```

Do I simply add this line to the bottom?
Not sure what the "1" and "2" mean?
```
LABEL=/home     /home   ext4    defaults,grpquota,usrquota       1       2
```

Or am I supposed to change the UUID=0ab56e90-db11-4ada-9844-a2d56d570c30 line?
No you can't just add a line for a quota anywhere.  The quota needs to be applied to a partition.  In your case the only viable partition is / ( see above in red).  As @kerry_s mentions, you do not have a separate partition for /home so you can't place a quota.

The tutorial you are using is for RedHat, not Ubuntu.  You are better off using [**this tutorial**]("https://www.howtoforge.com/tutorial/linux-quota-ubuntu-debian/").

---

### Post by snakyjake on 2015-08-14
What are my options for putting a quota on the /home directory?
Other tool?
Can I create a /home partition?  Is there a stupid simple how-to?

Thanks in advance.

---

### Post by bab1 on 2015-08-14
> **snakyjake said:**
> What are my options for putting a quota on the /home directory?
Other tool?
Can I create a /home partition?  Is there a stupid simple how-to?

Thanks in advance.
The quota must go on a partition, not just the file system on the partition.  A partition is really just the container for the file system.  The quota is for the container and the file system at that container.  If you want to create a new partition and mount it at /home you would either have to reduce the size of the / (root partition by a corresponding) amount to create the new partition or buy another device to format the new file system (ext4) and mount it at /home.   You would have to move all the data at the current /home before you mount the new partition at that location.  You should always have a backup of your data in any case.  Do you have a backup of all your data?

There are plenty of guides to do either one of these tasks.  You have to decide which method you want to do first.  It is either carve out a partition from existing HDD or new HDD with partition).  Neither are what you would call simple tasks.

---

### Post by snakyjake on 2015-08-14
Thanks for the hint.  I'll do some more research.

---

