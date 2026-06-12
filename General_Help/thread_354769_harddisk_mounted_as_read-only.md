---
title: "harddisk mounted as read-only"
date: 2007-02-06
forum: General Help
---

### Post by stiankarlsen on 2007-02-06
I use fstab to mount my harddrives, and when I boot the PC, everything works fine, and I can write to all harddrives, after some time, don't know how long, some hours i guess, /dev/sdb1/ becomes read-only.


> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdf        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3 /media/140a ext3
/dev/sdb1 /media/300a ext3
/dev/sdc1 /media/200a ext3 


What is going on?

---

### Post by taurus on 2007-02-06
That is an odd looking /etc/fstab.  Personally, I would have made it look like this.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hdf /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda3 /media/140a ext3 defaults 0 1
/dev/sdb1 /media/300a ext3 defaults 0 1
/dev/sdc1 /media/200a ext3 defaults 0 1

```

---

### Post by kebes on 2007-02-06
Well it doesn't make much sense to me that it works for awhile and then eventually stops...

However the last three lines of your fstab look strange because they have no options set for them. Normally they would look more like:
```

/dev/sda3 /media/140a ext3   defaults   0   2
/dev/sdb1 /media/300a ext3   defaults   0   2
/dev/sdc1 /media/200a ext3   defaults   0   2

```

You could try making that change and see if that fixes it. (Instead of defaults you can put the options which explicitly give users permission to read and write...)

---

