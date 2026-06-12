---
title: "my fstab info doesnot match /dev/disk/by-uuid info"
date: 2008-04-06
forum: General Help
---

### Post by ashjas on 2008-04-06
Hi,

my fstab info doesnot match /dev/disk/by-uuid info...

here is my fstab info::
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=1b5a38ca-9f0d-4f1a-8fc1-7c418e79bf07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9CD81843D8181E58 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=C5C6-7B7C  /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=E9FF-E1BE  /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=ab4ea8ac-45cc-4e71-b188-a52e6ca0523c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and this is what ls -l /dev/disk/by-uuid  shows::
```

total 0
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 1b5a38ca-9f0d-4f1a-8fc1-7c418e79bf07 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 6EFC5123FC50E73D -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 7DD0-6495 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 8E65816F3E61B0D6 -> ../../sda8
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 ab4ea8ac-45cc-4e71-b188-a52e6ca0523c -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-06 23:00 B26F6609D645FCBE -> ../../sda9

```

note that sda7 in ls-l is shown as sda8 in fstab file with the same uuid...how is this possible...i have always been surprised by the way linux identifies the partitions ...once there was a case i remember where while at linux desktop,linux ext3 partition was shown as sda8  but in the menu.lst it had to be configured as sda7 for the grub to boot ubuntu...can anyone give me a clue??

i recently re organised my partitions so now ubuntu doesnt mount those partitions automatically...maybe there is a mismatch of the uuids of the partitions in the fstab file....


can anuone give me any idea how to fix this uuid mess and re-automount my other partitions on ubuntu??


Thanks for the help..

---

### Post by logos34 on 2008-04-06
You might want to post output of **sudo fdisk -l **and **mount**.

It's clear that swap and root are fine.  Just the the ntfs (logical) partitions 1,6,8 need fixing  (+ mount points)  

First, backup the file, then correct / entry:

sudo cp /etc/fstab /etc/fstab.bak

gksudo gedit /etc/fstab

> # /dev/sda**[COLOR="Red"]7[/COLOR]**
UUID=1b5a38ca-9f0d-4f1a-8fc1-7c418e79bf07 /               ext3    defaults,errors=remount-ro 0       1
 
Delete the ntfs entries or comment them out (#), then run ntfs-config

sudo apt-get install ntfs-config

sudo ntfs-config


---------
Manually (more complicated):

remove the UUIDs and use the /dev/sda? format:

Ex:
> /dev/sda1 /media/sda1 ntfs defaults,umask=007,gid=46 0 1

OR 

Use tune2fs to manually change the UUIDs:

**sudo tune2fs -U random /dev/sda1**

then check new # with** blkid** or **sudo vol_id -u /dev/sda1** and replace edit fstab.  Change mount points accordingly (sudo mkdir)

---

