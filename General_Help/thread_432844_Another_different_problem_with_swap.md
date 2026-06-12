---
title: "Another different problem with swap"
date: 2007-05-04
forum: General Help
---

### Post by boobis on 2007-05-04
After upgrading to Edgy (from LTS) suspend stopped working (as documented elsewhere).

After upgrading to Feisty it didn't come back so I decided to fix it. After searching here and on launchpad i used the solution everyone seems to use, make new swap, record UUID, update initramfs-tools etc. etc. And now suspend works. BUT:

```
jbf@deep:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       2096472 0       -1
/dev/mapper/sda3                        partition       2096472 0       -2
jbf@deep:~$ 
```

isn't this kind of funky?

fdisk -l says:

```
jbf@deep:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1992    16000708+   c  W95 FAT32 (LBA)
/dev/sda2            1993        4603    20972857+  83  Linux
/dev/sda3            4604        4864     2096482+  82  Linux swap / Solaris
jbf@deep:~$ 
```

vol_id:

```
jbf@deep:~$ sudo vol_id /dev/sda3
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=62233fed-93b6-47de-9bcd-b730c9a10bd6
ID_FS_LABEL=
ID_FS_LABEL_SAFE=
jbf@deep:~$ 

```

and /etc/fstab:

j```
bf@deep:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=3440-10F6 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
UUID=62233fed-93b6-47de-9bcd-b730c9a10bd6 none swap sw 0 0
UUID=fc34bfe5-6bce-4541-8a5b-08d4bf73b586 / ext3 defaults,errors=remount-ro 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
jbf@deep:~$ 
```

Oh, it's an IBM x40 with 40 GiB of disk and fairly new BIOS.

My worries is that if I ever use more than 2G of swap (firefox anyone ;) ) it will overwrite the first (same) swap and nothing good can come out of that.

(I haven't filed a bug.)

Anyone got the same problem?

---

### Post by boobis on 2007-05-04
Btw free really thinks it got twice the actual swap:

```
jbf@deep:~$ free
             total       used       free     shared    buffers     cached
Mem:        506776     444752      62024          0      11796     232452
-/+ buffers/cache:     200504     306272
Swap:      4192944          0    4192944
jbf@deep:~$
```

---

### Post by Sod75 on 2007-05-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86234](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86234) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				fyi
I've got exactly the same issue, I also got it in the same way you describe.
If i do 
swapoff -a
swapon -a
all is ok again

there's already a bug open too

---

