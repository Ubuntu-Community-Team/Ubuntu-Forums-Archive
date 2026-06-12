---
title: "Changing Xubuntu Mount Points"
date: 2007-01-21
forum: General Help
---

### Post by Pobega on 2007-01-21
I'm trying to change my Xubuntu's mount points from /media to /mnt (/mnt **is** the /mount folder after all), but I have no idea how to do it. Currently the only things I'm needing to mount is my CD drive (scd0, I think) and my USB Drive (sdb1 and sdb2). I'm not sure if this all belongs in the fstab, but I didn't want to jump to any conclusions since editing my fstab could really mess up my computer.

For the record though, my fstab is:> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ba00e0e2-d7c2-4be3-a24b-4548df2e1f6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1e90b0a0-4100-4051-a315-83370313745b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

---

### Post by rianquinn on 2007-01-21
In your fstab you need to change the /media to /mnt

---

### Post by kerry_s on 2007-01-21
Just change media to mnt, then create the folders for the device in mnt just like it is in media(you can just copy or cut the folders in media to mnt)

Why not just leave it as it is and create a link from mnt to media.

example:

sudo rm -r /mnt
sudo ln -s /media /mnt

---

### Post by Pobega on 2007-01-21
> **rianquinn said:**
> In your fstab you need to change the /media to /mnt

So could I make my fstab something like this?
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# internal storage devices
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/sda3 /home ext3 nodev,nosuid 0 2

# cd drive
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

# external storage devices
/dev/sdb1 /mnt/usbdisk udf,iso9660 user,noauto 0 0
/dev/sdb2 /mnt/feather udf,iso9660 user,noauto 0 0

(The reasoning for this is because most flash cards will show up as /dev/sdb1, and on mine my second partition [sdb2] is a FeatherLinux install.)

Also, what would I do for mounting my iPod to /mnt/ipod?

---

### Post by kerry_s on 2007-01-21
Is your system not auto mounting? External drives are handled by mtab, when you plug it in it will create the mount point and folder. If you choose to by pass it you might get mounting errors or errors at boot when there not plugged in. If it's not auto mounting try installing> ivman <to take care of auto mounting.

You should not need to worry about duplicate sd?? drives the computer would simply move on to the next available sd??

---

### Post by Pobega on 2007-01-21
Well yeah, I know that, but all I want to do is move everything from /media to /mnt. I don't see the point in having two folders for mounting things to.

---

### Post by kerry_s on 2007-01-22
Only /media is used for mounting you could delete /mnt altogether and it won't make a difference. You can follow my other suggestion and just link /mnt to /media just in case and app looks for your drives in /mnt. I think you trying to change the location may cause problems later down the line if there are security updates, your system won't boot.

You can also do it the other way around and move all the files to /mnt then link /media to /mnt.

Any which way you choose you will still need a /mnt and /media so your basically just going around in circles.

---

### Post by Pobega on 2007-01-22
> **kerry_s said:**
> Only /media is used for mounting you could delete /mnt altogether and it won't make a difference. You can follow my other suggestion and just link /mnt to /media just in case and app looks for your drives in /mnt. I think you trying to change the location may cause problems later down the line if there are security updates, your system won't boot.

You can also do it the other way around and move all the files to /mnt then link /media to /mnt.

Any which way you choose you will still need a /mnt and /media so your basically just going around in circles.

Hm, I'll just leave it alone and live with it then.

---

