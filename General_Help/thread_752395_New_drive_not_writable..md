---
title: "New drive not writable."
date: 2008-04-11
forum: General Help
---

### Post by robfindlay on 2008-04-11
I just installed a new Seagate Barracuda 500 gig drive as a secondary slave.  Ran gparted to partition and format it for ext3 i boot up, i can see the drive, yet I cannot write to it. 

Here is my FSTAB. 

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# /dev/sda1
UUID=1b2887e4-c843-4554-b435-f141a6f43ec9  /               ext3         errors=remount-ro         0  1  
# /dev/sda5
UUID=601b62b5-784d-4397-a66b-7390e9810425  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     vfat         defaults                  0  0   


Any ideas?

---

### Post by robfindlay on 2008-04-11
this doesn't make any sense the new drive is not in the FSTAB i mount it manually and still cant write to it. 

Then I go and chmod 777  the directory it's in and now i can write to it.

Weird.

---

### Post by plucky on 2008-04-11
See [this link](http://www.psychocats.net/ubuntu/mountlinux) for more information.

Good Luck

---

### Post by cdenley on 2008-04-11
The drive has it's own filesystem with it's own unix permissions. You aren't chmod'ing the directory it's in, your chmod'ing the root directory of your new filesystem.

---

