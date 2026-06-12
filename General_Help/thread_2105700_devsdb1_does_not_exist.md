---
title: "/dev/sdb1 does not exist"
date: 2013-01-16
forum: General Help
---

### Post by davidmenges on 2013-01-16
My 12.04 Server suddenly doesn't want to mount one of my internal drives.  Upon boot it says "The disk drive for /media/hd2 is not ready yet or not present.".

The strange thing is I can cd into /media/hd2, and I see everything - files and folders.  However, ls -l /dev/sdb1 says "no such file or directory".

My /etc/fstab looks good, but my /etc/mtab doesn't have a line for /dev/sdb1.  When I add it manually (every time I boot), df then has an entry for /media/hd2 but /dev/sdb1 still doesn't exist.

Hints?  I'll buy you a six pack...

---

### Post by bab1 on 2013-01-16
> **davidmenges said:**
> My 12.04 Server suddenly doesn't want to mount one of my internal drives.  Upon boot it says "The disk drive for /media/hd2 is not ready yet or not present.
The strange thing is I can cd into /media/hd2, and I see everything - files and folders.  However, ls -l /dev/sdb1 says "no such file or directory".

My /etc/fstab looks good, but my /etc/mtab doesn't have a line for /dev/sdb1.  When I add it manually (every time I boot), df then has an entry for /media/hd2 but /dev/sdb1 still doesn't exist.

Hints?  I'll buy you a six pack...

The files in /dev define the various devices.  The partition sda1 is a block device.  It holds data in blocks.  The command *ls* will list the device as such```
**[COLOR="Red"][SIZE="2"]b[/SIZE][/COLOR]**rw-rw---- 1 root disk 8, 1 Jan 16 10:31 /dev/sda1

```

Note the **[COLOR="Red"]b[/COLOR]** on the far left.  This connotes that this is a block device.  The user can't see any information like you would see in a directory.  See a directory listing here ```

**[SIZE="2"][COLOR="Blue"]d[/COLOR][/SIZE]**rwxr-xr-x 2 bab bab 4096 Jan 15 20:29 Desktop
**[SIZE="2"][COLOR="Blue"]d[/COLOR][/SIZE]**rwxr-xr-x 5 bab bab 4096 Nov 11 14:20 Documents

```
Note the **[COLOR="Blue"]d[/COLOR]** at the far left.  This connotes a directory that holds data the *[COLOR="Blue"]can[/COLOR]* be seen by the user.

In short /dev files are for OS interface with devices, not for the user to use directly.

---

### Post by ajgreeny on 2013-01-16
Lets see the output of ```
sudo blkid -c /dev/null
sudo fdisk -l
cat /etc/fstab
``` one by one please.

---

### Post by fdrake on 2013-01-16
it looks like your partition is being mounted with a different part name:
try
```

less /etc/mtab | grep "/media/"

```

@ajgreeny  blkid doean't need sudo: ;)

---

### Post by ajgreeny on 2013-01-17
> **fdrake said:**
> @ajgreeny  blkid doean't need sudo: ;)
It does on my system!

No sudo; no output!

---

### Post by Warren Hill on 2013-01-17
first step is to make sure your system can see it and check if its mounted or not 

```

sudo fdisk -l; mount | grep ^'/dev'

```

If its there but not mounted edit /etc/fstab 
see here [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by davidmenges on 2013-01-19
> **ajgreeny said:**
> Lets see the output of ```
sudo blkid -c /dev/null
sudo fdisk -l
cat /etc/fstab
``` one by one please.

OK, here goes.  I notice /dev/sdb1 is missing from blkid...  I don't have data on that drive, so I can reformat - if I thought it would help.

blkid:

/dev/sda1: UUID="e48a840e-28f9-4c31-9e66-30fd1aa1696b" TYPE="ext2" 
/dev/sda5: UUID="uMu31h-Vvh6-Nmdi-C0b3-RS1K-JIzG-yb6i8W" TYPE="LVM2_member" 
/dev/sdc1: LABEL="hd3" UUID="c79fbd4f-b8d5-46dd-9b4d-62afa6050a69" TYPE="ext4" 
/dev/sdd1: LABEL="hd4" UUID="57fdc863-d21d-4a07-9fc9-6b674ecb51b2" TYPE="ext4" 
/dev/mapper/davidubu-root: UUID="00508efc-5664-49a9-81f7-718e2315e404" TYPE="ext4" 
/dev/mapper/davidubu-swap_1: UUID="49ac5e7f-3d3e-4f00-84a2-6da3655faeaf" TYPE="swap"

fdisk:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT

Disk /dev/mapper/davidubu-root: 995.6 GB, 995606134784 bytes
255 heads, 63 sectors/track, 121042 cylinders, total 1944543232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/davidubu-swap_1: 4290 MB, 4290772992 bytes
255 heads, 63 sectors/track, 521 cylinders, total 8380416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/davidubu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e48a840e-28f9-4c31-9e66-30fd1aa1696b /boot           ext2    defaults        0       2
/dev/mapper/davidubu-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Added by David C. Menges 2012-10-24
/dev/sdb1 /media/hd2 ext4 defaults 0 0
/dev/sdc1 /media/hd3 ext4 defaults 0 0
/dev/sdd1 /media/hd4 ext4 defaults 0 0

---

