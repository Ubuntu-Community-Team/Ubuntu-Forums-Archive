---
title: "my mounting mishap [Resolved]"
date: 2007-05-16
forum: General Help
---

### Post by hgp on 2007-05-16
Hi, I just switched to a 100% Ubuntu environment (kicked the windows habit) and was trying to get my ipod to work. I was using gtkpod and it couldn't detect my ipod. I realized that my ipod was mounting at /media/ANDYS IPOD and not /media/ipod. I then, being very new at this, right clicked on the ipod and saw under the options to change the mounting point. Unfortunately, I mistyped the mount point and entered something invalid. Now, whenever I plug in my ipod it gives me an error saying that I have an invalid mount point, but it will not let me right click on it to change it. I think (hope) that there is some terminal magic that can save me, but I have no idea what it is.

---

### Post by aysiu on 2007-05-16
Can you plug the iPod in, paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
df -h
/etc/fstab
```

---

### Post by hgp on 2007-05-16
after: **sudo fdisk -l**
```

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 912 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           3       96264    0  Empty
/dev/sdc2               4         912    29206170    b  W95 FAT32

```

after: **df -h**
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              33G  3.0G   28G  10% /
varrun                502M   96K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  124K  502M   1% /proc/bus/usb
udev                  502M  124K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             147G  259M  140G   1% /home

```

and **/etc/fstab** contains:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d4ed6260-dd46-4a68-a904-8771de3678be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=318e92f2-ce00-42e0-a783-4d8c3e2a2ccb none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /home ext3 defaults,errors=remount-ro 0 1

```

thanks for looking at this!

---

### Post by aysiu on 2007-05-16
Leave your iPod plugged in.

Can you try pasting these commands into the terminal? ```
sudo mkdir /media/ipod
sudo mount -t vfat /dev/sdc2 /media/ipod -o iocharset=utf8,umask=000
``` and see if that works?

---

### Post by hgp on 2007-05-16
It worked.
Thank you so much, you're a life saver!

---

### Post by aysiu on 2007-05-16
Great to hear!

---

### Post by ANTDx1 on 2007-05-24
This solution also works for me.  However, I am unable to change the default mount point to media/ipod, so I have to mount it like this every time.  While this is no problem for me, it will pose a problem for my brother, who also uses his ipod, and has no idea how to manually mount a device.

---

### Post by alex_anthony on 2007-06-01
put the command into a script and call it 'mount-ipod.sh' or something. Put it on the desktop, link to it if you need it in other places, tell him just to click that when he needs to mount it

---

