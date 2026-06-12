---
title: "Mounting Drives Based off UUID"
date: 2008-03-27
forum: General Help
---

### Post by Tixer on 2008-03-27
I have two identical hard drives, in two identical enclosures, and I need a way to make sure that there isn't a 50/50 chance of what gets mounted as /media/disk / /media/disk-1. I was told I could do this using /etc/fstab, but I have no idea what to do.

Omgwtfhax:~$ blkid
/dev/sda1: UUID="e6278f0e-6ca0-4032-8650-2021f152143b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="a46176be-c04c-44c2-98d7-3c7b579732ef"
/dev/sdc1: UUID="FEBC6652BC66058D" TYPE="ntfs"
/dev/sdb1: UUID="D28483DC8483C209" TYPE="ntfs"

I'd like to mount /dev/sdb1 to /media/black, and /dev/sdc1 to /media/blue. Here is my current fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6278f0e-6ca0-4032-8650-2021f152143b /               ext3    defaults,error      s=remount-ro 0       1
# /dev/sda5
UUID=a46176be-c04c-44c2-98d7-3c7b579732ef none            swap    sw                    0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by nick_h on 2008-03-27
Try adding:
```

# /dev/sdb1
UUID=D28483DC8483C209    /media/black    ntfs    defaults,umask=007,gid=46    0    1

```
and a similar line for the other filesystem.

---

### Post by danwood76 on 2008-03-27
you could also re label the disks which would then create them different mount points.

---

### Post by stchman on 2008-03-27
> **Tixer said:**
> I have two identical hard drives, in two identical enclosures, and I need a way to make sure that there isn't a 50/50 chance of what gets mounted as /media/disk / /media/disk-1. I was told I could do this using /etc/fstab, but I have no idea what to do.

Omgwtfhax:~$ blkid
/dev/sda1: UUID="e6278f0e-6ca0-4032-8650-2021f152143b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="a46176be-c04c-44c2-98d7-3c7b579732ef"
/dev/sdc1: UUID="FEBC6652BC66058D" TYPE="ntfs"
/dev/sdb1: UUID="D28483DC8483C209" TYPE="ntfs"

I'd like to mount /dev/sdb1 to /media/black, and /dev/sdc1 to /media/blue. Here is my current fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6278f0e-6ca0-4032-8650-2021f152143b /               ext3    defaults,error      s=remount-ro 0       1
# /dev/sda5
UUID=a46176be-c04c-44c2-98d7-3c7b579732ef none            swap    sw                    0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

You don't need the UUIDs.  I find them fairly useless.

Do the following:

```

sudo mkdir /media/black
sudo mkdir /media/blue

```

Enter these lines in your fstab file as root.
/dev/sdb1     /media/black    ntfs  nls=utf8,umask=0222  0   0
/dev/sdc1     /media/blue    ntfs  nls=utf8,umask=0222  0   0

If you want to be able to write to these partitions then install the ntfs-3g package and change the lines as follows.

First install the ntfs-config package.
```
sudo apt-get instlall ntfs-config
```

Then edit the fstab file using sudo
/dev/sdb1     /media/black    ntfs-3g  defaults  0   0
/dev/sdc1     /media/blue    ntfs-3g  defaults  0   0

Hope this helps.

---

### Post by Tixer on 2008-03-27
> **stchman said:**
> You don't need the UUIDs.  I find them fairly useless.

Do the following:

```

sudo mkdir /media/black
sudo mkdir /media/blue

```

Enter these lines in your fstab file as root.
/dev/sdb1     /media/black    ntfs  nls=utf8,umask=0222  0   0
/dev/sdc1     /media/blue    ntfs  nls=utf8,umask=0222  0   0

If you want to be able to write to these partitions then install the ntfs-3g package and change the lines as follows.

First install the ntfs-config package.
```
sudo apt-get instlall ntfs-config
```

Then edit the fstab file using sudo
/dev/sdb1     /media/black    ntfs-3g  defaults  0   0
/dev/sdc1     /media/blue    ntfs-3g  defaults  0   0

Hope this helps.

I thought I needed the UUIDs to make sure that there isn't a random chance of where the drive mounts. Both drives turn on randomly when I reboot, so there's usually a 50% chance that the blue drive will mount as /dev/sdb1. I need to make sure that if I have an application that has a hard-coded path, it'll mount in the right place.

---

### Post by Tixer on 2008-03-27
> **nick_h said:**
> Try adding:
```

# /dev/sdb1
UUID=D28483DC8483C209    /media/black    ntfs    defaults,umask=007,gid=46    0    1

```
and a similar line for the other filesystem.

Can you explain what the line "defaults,umask=007,gid=46    0    1"  does? I want all users to have full permissions.

---

### Post by chrisccoulson on 2008-03-27
> **Tixer said:**
> I thought I needed the UUIDs to make sure that there isn't a random chance of where the drive mounts. Both drives turn on randomly when I reboot, so there's usually a 50% chance that the blue drive will mount as /dev/sdb1. I need to make sure that if I have an application that has a hard-coded path, it'll mount in the right place.

UUID's are a more robust way of mounting static filesystems, as a physical device may not always get the same device node, especially if you have external disks / pen drives which may or may not be connected (or may be connected in different USB ports etc) when you boot the machine.

---

### Post by chrisccoulson on 2008-03-27
> **Tixer said:**
> Can you explain what the line "defaults,umask=007,gid=46    0    1"  does? I want all users to have full permissions.
```
defaults,umask=007,gid=46
```
...sets default mount options (rw,suid,dev,exec,auto,nouser,async), makes the mounted volume owned by the plugdev group (which you should belong to), and will set 770 permissions for the volume (which will give full read-write-execute access to all members of the plugdev group)

The number at the end specifies the order in which fsck scans the volumes when you boot the machine up. You already have a '1' in your fstab, so you should make your volumes '2' and '3' I think (or set to '0' to disable fsck on these volumes)

Have a look here: [http://en.wikipedia.org/wiki/Fstab]("http://en.wikipedia.org/wiki/Fstab")

---

### Post by dcstar on 2008-03-27
> **danwood76 said:**
> you could also re label the disks which would then create them different mount points.

Exactly, why do something over-complicated when a simple disk label will do the job?

Putting external drives in the fstab seems problematic to me, as you can get issues on boot-up if these drives are not plugged in (and usable at that stage).

---

### Post by stchman on 2008-03-28
> **Tixer said:**
> I thought I needed the UUIDs to make sure that there isn't a random chance of where the drive mounts. Both drives turn on randomly when I reboot, so there's usually a 50% chance that the blue drive will mount as /dev/sdb1. I need to make sure that if I have an application that has a hard-coded path, it'll mount in the right place.

That could very well be true, I have just a single drive system so there is no chance of what you are taking about happening.

---

### Post by danwood76 on 2008-03-28
Re-label the drives, its the best and simplest solution, heres the community doc on the subject:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

