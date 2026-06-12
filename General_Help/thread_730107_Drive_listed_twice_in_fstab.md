---
title: "Drive listed twice in fstab"
date: 2008-03-20
forum: General Help
---

### Post by pantherattack on 2008-03-20
Hi,

I have two hard drives. The first has partitions sda1 and sda5 (windows is installed on sda1). The second has my ubuntu install and the partition sdb3.

When I start up, first it mentions that sda1 is clean and tells me how many mounts until it will do a check. Then it mentions sbd3 and pauses for a really long time. It then prints about 10 lines of hexidecimal numbers and says that it "Will not automatically fix this."

Then it mentions sda1 again. It goes a bit too fast for me to read what it's doing.

I have no problems with any drives, but  the long pause makes up more than half of my boot time, which is annoying.

I'm wondering which drive is giving the issues. My fstab for some reasons has two lines devoted to sda1. My fstab is as follows and has never been altered:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=147d2686-16ac-4942-91b2-e961d2894332 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2C3A-EBE0  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=16BC6769BC67427B /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=CF29-F70C  /media/sdb3     vfat    defaults,utf8,umask=007,gid=46,check=r 0       1
# /dev/sdb2
UUID=c0529bc2-a37a-42b8-98a0-576856a1cd9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Thanks for any help.

---

### Post by forestpixie on 2008-03-20
I can't see 2 lines? Can you highlight which 2 you see.

---

### Post by pointone on 2008-03-20
The error messages should be logged in dmesg. You can also use scroll lock to pause the boot process and get a better look at the messages.

Without the exact error messages, we can't really help much.

---

### Post by forestpixie on 2008-03-20
> You can also use scroll lock to pause the boot process and get a better look at the messages.

I ALWAYS learn something new when I'm here :D

---

### Post by HunterK on 2008-03-20
> **forestpixie said:**
> I can't see 2 lines? Can you highlight which 2 you see.

Please do.  You had me questioning my eyesight there for a while.  I see no "double" listing.  I see /dev/sdb1 and /dev/sda1

---

### Post by forestpixie on 2008-03-20
Had a think from a new point of view so perhaps the OP means

# /dev/sda1 and the UUID=2C3A-EBE0  /media/sda1

in which case # /dev/sda1 is jsut a comment line and as pointone says we need more info

---

