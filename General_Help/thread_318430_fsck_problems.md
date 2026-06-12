---
title: "fsck problems"
date: 2006-12-14
forum: General Help
---

### Post by nmatheis on 2006-12-14
hello all!

i have my hd divided up as an extended partition with hda1 as swap and hda5-10 as logical partitions for testing out distros.  i recently installed opensuse 10.2 to try it out.  after the install, when i tried to boot ubuntu it hung at the boot splash screen.  after a minute or so, it switched over to verbose mode and indicated that there was a problem with fsck involving hda8 (the partition opensuse is on).  the weird thing is, i issued the **shutdown -r now** command to restart the computer.  instead of shutting down the computer though, it just went to the ubuntu login screen.  i have tried rebooting into ubuntu a few times, and every time it hangs - and every time issuing the **shutdown -r now** command gets me to the login screen for ubuntu.  i'm logged in and writing this post from ubuntu right now.  my question is how can i get this problem fixed so that i don't have to issue the ** shutdown -r now** command every time?

here's my fstab file, if that will help: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=7708bb1b-4c4a-43f9-864e-552e81833a0c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda10
UUID=4346b520-144a-438f-8098-34f495411897 /dev/hda10      ext3    defaults        0       2
# /dev/hda9
UUID=4942c0ea-9fca-4e68-a950-005afed07dc2 /dev/hda9       ext3    defaults        0       2
# /dev/hda5
UUID=42bbd1b4-b38e-4fca-ade5-275fbe733870 /mnt/PCLOS    ext3    defaults        0       2
# /dev/hda6
UUID=55cb07ad-5070-402c-907f-a9989669a526 /mnt/Share    ext3    defaults        0       2
# /dev/hda8
UUID=54a70676-594d-4128-8dc2-eb7fe4bf08bf /mnt/openSUSE    ext3    defaults        0       2
# /dev/hda1
UUID=07631905-4727-4718-bd93-2be23081cb4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

thanks!
nikolaus

---

### Post by bodhi.zazen on 2006-12-14
Did you format the partition when you installed SUSE ?

The UUID may have changed.

Check by typing ```
ls /dev/disk/by-uuid -lh | grep hda8
```

Try unmounting and remounting the partition in a terminal to see if you aer getting any error messages:```
sudo umount /mnt/openSUSE
sudo mount /mnt/openSUSE 
```

Last try changing your fstab to:> # /dev/hda8
/dev/hda8 /mnt/openSUSE  ext3  defaults  0  2

---

### Post by nmatheis on 2006-12-14
> **bodhi.zazen said:**
> Did you format the partition when you installed SUSE ?

The UUID may have changed.

Check by typing ```
ls /dev/disk/by-uuid -lh | grep hda8
```

thanks for the tip!  i issued the command and saw a different UUID than the one listed in fstab.  i'll have to write that command down, as i've encountered this problem before (fsck problem + hanging at boot).  i replaced the old UUID for /dev/hda8 with the new UUID from the command you provided, and successfully mounted /dev/hda8 by issuing```
mount /mnt/openSUSE
```.  now i'll try rebooting into ubuntu :)

so what exactly is the UUID?  a unique identifier of some sort for the partition, i'm assuming?

thanks!
nikolaus

---

### Post by nmatheis on 2006-12-14
changing the uuid did it for me - thanks!

---

### Post by bodhi.zazen on 2006-12-14
UUID = Universally Unique Identifier

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

8)

---

