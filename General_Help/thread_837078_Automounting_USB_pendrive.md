---
title: "Automounting USB pendrive"
date: 2008-06-22
forum: General Help
---

### Post by botfish on 2008-06-22
I have installed Ubuntu 8.04 on an Dell Optiplex GX280. I installed 8.04 from a USB pen drive as I do not have a CD drive. Everything working well except USB drives would not automount (error: invalid mount option). I could manually mount from the command line no problem (sudo mount /dev/sdb1 /media/disk).

I commented out the last two lines in /etc/fstab and now my USB pen drives automount.

Can anyone tell me why this fixed my problem?
Will there be side effects?
Why are those last two lines in my /etc/fstab?
Can I delete the /media/cdrom0 and /media/cdrom1 directories?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ebf39968-03e1-4398-a954-221581c6f28e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9b1083c6-5b6e-4ce0-ab8b-2c35cd84f72e none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by PmDematagoda on 2008-06-22
Remove the following line in fstab:-
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=ebf39968-03e1-4398-a954-221581c6f28e / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=9b1083c6-5b6e-4ce0-ab8b-2c35cd84f72e none swap sw 0 0
**[COLOR="Red"]#/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0[/COLOR]**
#/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0 
```

That should fix the problem, if you don't have a CD-ROM, then there won't be a problem removing the scd0 line as well.

Whoops, forgot to answer the questions:-

1) When you plug a second internal/external drive, what I can suppose is that Ubuntu first uses fstab to see if there is an existing entry for it before attempting to mount it itself, so removing the line in question fixes the problem since sdb essentially refers to USB pen drives you plug in at one time, although if you plugged in another USB drive while one was already plugged in then no problem would have occurred since it would be sdc.

2) No, there shouldn't be any side-effects unless you decide to put in a CD-ROM one day.

3) Those two lines are automatically added during the install process when it detects the available hardware.

4) Yes you can, they are just essentially folders and if they were ever needed again you only have to create them with the same name as the corresponding entry in fstab.

---

