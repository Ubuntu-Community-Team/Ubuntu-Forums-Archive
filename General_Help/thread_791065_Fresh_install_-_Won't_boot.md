---
title: "Fresh install - Won't boot"
date: 2008-05-11
forum: General Help
---

### Post by MikeReiner on 2008-05-11
The installation of Ubuntu 8.04 went smoothly, I installed it to an 80gb western digital hard drive. No dual boot setup or anything like that, just ubuntu.

I installed Ubuntu 8.04 LTS Desktop Edition - Supported to 2011.

After the installation, it wouldn't boot. The ubuntu logo would load, and after about 5 seconds the HD activity LED stops blinking, about 5 minutes later, i get this:

BusyBox V1.1.3 (debian 1:1.1.3-5ubuntu12) built-in shell (ash)
Enter 'help' for a list of commands.

Upon pressing ctrl+alt+F1, i find this:

Starting up...
Loading, please wait ...
Checkroot= Bootarg cat /proc/cmdline or missing modules, devices: cat/proc/modules is /dev

Alert!
/dev/disk/by-uuid/92624db9-d108-4632-a426-a8003ee7bb69 does not exist.
Dropping to a shell!

Here is my hardware:
AMD64 X2 4200+
2gigs corsair DDR400
MIS K8N Neo4-F
GeForce 8800GT

---

### Post by ajmorris on 2008-05-11
hi there,
could you please boot into a live cd, and post your /etc/fstab file, and the output of sudo fdisk -l

AJ

---

### Post by MikeReiner on 2008-05-11
> **ajmorris said:**
> hi there,
could you please boot into a live cd, and post your /etc/fstab file, and the output of sudo fdisk -l

AJ

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by ajmorris on 2008-05-11
> **MikeReiner said:**
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

Surely that isnt the whole fstab? if so, this is your problem, no root device is specified to boot off.
Please post the output of sudo fdisk -l so we can add one :)

---

### Post by MikeReiner on 2008-05-11
> **ajmorris said:**
> Surely that isnt the whole fstab? if so, this is your problem, no root device is specified to boot off.
Please post the output of sudo fdisk -l so we can add one :)

Okie dokie.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x485b485b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55ec63c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS
ubuntu@ubuntu:~$

Edit: There, it helps if I actually copy the whole output..
The 80gb is where I installed ubuntu, and the 120gb is where all my data is from when I was using XP.

---

### Post by ajmorris on 2008-05-11
ok,
open up /etc/fstab as root,
and add this below your tmpfs line:

```
/dev/sda1               /               ext3        defaults  0 0 
```

However, where i have ext3, your filesystem may not be this, this is the default format used however, so is most likely this.

Also, before you reboot, could you please post your /boot/menu.lst file, i just want to check the root device is specified properly in it also.

AJ

---

### Post by MikeReiner on 2008-05-11
> **ajmorris said:**
> ok,
open up /etc/fstab as root,
and add this below your tmpfs line:

```
/dev/sda1               /               ext3        defaults  0 0 
```

However, where i have ext3, your filesystem may not be this, this is the default format used however, so is most likely this.

Also, before you reboot, could you please post your /boot/menu.lst file, i just want to check the root device is specified properly in it also.

AJ

That file does not exist.

---

### Post by ajmorris on 2008-05-11
> **MikeReiner said:**
> That file does not exist.

oh #@!@ sorry, im am half asleep, in my original post, where i asked you to post your fstab file, i meant the fstab from your ubuntu partition, not the live cd, you have to mount your partition first, please post your /media/ubuntu/etc/fstab and /media/ubuntu/boot/grub/menu.lst  where /media/ubuntu is where you mount your ubuntu partition.

AJ

---

### Post by MikeReiner on 2008-05-11
> **ajmorris said:**
> oh #@!@ sorry, im am half asleep, in my original post, where i asked you to post your fstab file, i meant the fstab from your ubuntu partition, not the live cd, you have to mount your partition first, please post your /media/ubuntu/etc/fstab and /media/ubuntu/boot/grub/menu.lst  where /media/ubuntu is where you mount your ubuntu partition.

AJ

Arhg, sorry, how do I mount my actual ubuntu installation?

---

### Post by ajmorris on 2008-05-11
```
sudo mkdir /media/ubuntu
```

```
sudo mount /dev/sda1 /media/ubuntu
```

---

### Post by MikeReiner on 2008-05-11
mount: special device /dev/sda1 does not exist

---

### Post by ajmorris on 2008-05-11
how strange... fdisk said your linux partition was /dev/sda1... it should work...

---

### Post by MikeReiner on 2008-05-11
ubuntu@ubuntu:~$ sudo mount /dev/sda/ /media/ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$

---

### Post by ajmorris on 2008-05-11
nah, /dev/sda is the block device for the actual hard disk, you have to mount the partition within the hard disk, which, fdisk said was /dev/sda1 for your linux... check fdisk -l again :)

---

### Post by MikeReiner on 2008-05-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x485b485b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55ec63c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/ubuntu
mount: special device /dev/sda1 does not exist
ubuntu@ubuntu:~$ 


I never have any luck when it comes to linux.

---

### Post by ajmorris on 2008-05-11
can you please post the result of ls -l /dev/sda1

also, consider running a check disk for errors on that partition
```
sudo fsck /dev/sda1
```
and post the output here.

---

### Post by MikeReiner on 2008-05-11
Ok, but I'll have to do that tomorrow. Night.

---

### Post by MikeReiner on 2008-05-12
ubuntu@ubuntu:~$ sudo ls -l /dev/sda1
ls: cannot access /dev/sda1: No such file or directory
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x485b485b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


I don't get it man...

---

### Post by ajmorris on 2008-05-12
that is just weird, looks as though your partition table is mucked up, i suggest a fresh install of ubuntu

---

