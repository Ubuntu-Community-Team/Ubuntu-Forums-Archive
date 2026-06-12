---
title: "fsck status 8 error"
date: 2007-07-05
forum: General Help
---

### Post by mpgarate on 2007-07-05
Im getting this error when booting (this was logged to /var/log/fsck/checkfs)

Log of fsck -C -R -A -a 
Thu Jul  5 12:34:24 2007

fsck 1.40-WIP (14-Nov-2006)
/media/MyStuff: clean, 6737/13526784 files, 5394172/27000832 blocks (check in 2 mounts)
fsck.ext3: Unable to resolve 'UUID=5fbd7372-1f1d-4554-9ada-3f3534790b05'

fsck died with exit status 8

Thu Jul  5 12:34:24 2007
----------------

then my partitions are all screwy once im booted up

---

### Post by confused57 on 2007-07-05
The UUID may have changed on this partition, this should help:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

Basically, you'll need to run the command "blkid" to determine your current UUID's, then compare the UUID's listed in your /etc/fstab & /boot/grub/menu.lst.

---

### Post by mpgarate on 2007-07-05
blkid returned:
> /dev/sda1: LABEL="/media/LinuxMint" UUID="a4d05077-b5d9-4fad-a023-91427098026e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="/media/MyStuff" UUID="9585e76a-d950-4f61-93ab-9f83a24979c0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="/" UUID="214f8b1e-8599-4c69-a630-4865acb94c46" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a5b1de7f-2d27-42ce-a920-daa504b50209" 
/dev/sdb1: LABEL="H10" UUID="F081-AC7D" TYPE="vfat" 


MyStuff is the partition with problems

my fstab is

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a4d05077-b5d9-4fad-a023-91427098026e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=9585e76a-d950-4f61-93ab-9f83a24979c0 /media/MyStuff  ext3    defaults        0       2
# /dev/sda4
UUID=5fbd7372-1f1d-4554-9ada-3f3534790b05 /media/Sabayon  ext3    defaults        0       2
# /dev/sda5
UUID=a5b1de7f-2d27-42ce-a920-daa504b50209 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

and my root partition was the only one I could find in the grub menu, and it was correct.

where do I go from here?

---

### Post by confused57 on 2007-07-05
Looks like your /dev/sda4 UUID has changed...just copy & paste the new UUID from "blkid" to your /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=a4d05077-b5d9-4fad-a023-91427098026e / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
UUID=9585e76a-d950-4f61-93ab-9f83a24979c0 /media/MyStuff ext3 defaults 0 2
# /dev/sda4
UUID=**214f8b1e-8599-4c69-a630-4865acb94c46** /media/Sabayon ext3 defaults 0 2
# /dev/sda5
UUID=a5b1de7f-2d27-42ce-a920-daa504b50209 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by mpgarate on 2007-07-05
done. rebooting. thanks for your help

---

