---
title: "[SOLVED] Can't Access USB HD"
date: 2008-07-03
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-07-03
Hi @ all.
Since I can't watch DVD's at the moment (see here [http://ubuntuforums.org/showthread.php?t=848096]("http://ubuntuforums.org/showthread.php?t=848096")) I thought I check my new external USB hard drive which I want to use for backups. But I can't access that drive.
It's brand new, formated with NTFS (ya ya ya, I know but that's how they come...) which should really be a problem at least to mount and get read access.
But if I can't mount the drive how can I even possibly reformat it? Can anyone help what to do? I never had that problem with other drives. At least I could get read access.
I really don't know what to do anymore. Almost feels like my system is sort of messed up. Can that really be? :confused:

---

### Post by justleen on 2008-07-03
Actually.. to reformat it shouldnt be mounted :0

Can you post he output of ```
 sudo fdisk -l 
```

---

### Post by Linux&amp;Gsus on 2008-07-03
Here is the fdisk -l output

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0e2040a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3649    29310561    7  HPFS/NTFS
/dev/sda2            3650        5473    14651280   83  Linux
/dev/sda3           12040       12161      979965   82  Linux swap / Solaris
/dev/sda4            5474       12039    52741395   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

sda1 is a WinXP partion. I need it for checking websites.
Thanks for your quick reply...

---

### Post by justleen on 2008-07-03
that looks fine...

how about this?
```

mount -t ntfs-3g /dev/sdb1 /mnt  
```
is that producing errors?

---

### Post by Linux&amp;Gsus on 2008-07-03
Here the output:

```
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt ntfs-3g defaults,force 0 0

```

I did that as root. As "normal" user it just said: "mount: only root can do that". Oh, and yes, I actually have a "real" root account.

---

### Post by justleen on 2008-07-03
try option 2
mount -t ntfs-3g /dev/sdb1 /mnt -o force

check first with "mount -l |grep sdb" that its not mounted

---

### Post by Linux&amp;Gsus on 2008-07-03
Here it is:

```
root@Ephesus:~# mount -l |grep sdb
root@Ephesus:~# mount -t ntfs-3g /dev/sdb1 /mnt -o force
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
root@Ephesus:~# mount -t ntfs-3g /dev/sdb1 /mnt -o force
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sdb1 (New Volume)

```

---

### Post by justleen on 2008-07-03
so that worked? apart from you running it twicem so it unmounts again?

---

### Post by Linux&amp;Gsus on 2008-07-03
Ups, I didn't realize at first that it worked. My bad.
Thank you so much.

Uhmmm, would you mind explaining what actually happened? I guess I still don't really figured out what the problem is/was. That's probably why I didn't realize that it' actually working.


Thanks again for your help.

---

### Post by justleen on 2008-07-03
not sure.. apperently you need the -force option.

THe default mount doenst do that, thus it wasnt mounted..

---

### Post by Linux&amp;Gsus on 2008-07-03
Well, then so be it. As long as it works.
Will see now how I partition that thing and set up the backup. Uhm, and figure out how to mark a thread as solved... :)

---

