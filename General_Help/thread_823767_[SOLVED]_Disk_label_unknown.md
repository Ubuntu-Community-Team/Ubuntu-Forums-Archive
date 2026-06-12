---
title: "[SOLVED] Disk label unknown?"
date: 2008-06-09
forum: General Help
---

### Post by graabein on 2008-06-09
Hi, I have a SATA-disk that shows up with its size and not a label name on my desktop and in Nautilus. Is there any way I can safely give it a name without erasing the entire disk?

Right-clicking in Nautilus shows the rename option as grayed out...

---

### Post by drs305 on 2008-06-09
You can label a partition with **e2label**.

```
sudo e2label /dev/**sda2** **name**
```

After creating the name, you can try these commands to get it to show or you may have to reboot. It depends on what partition it is:

```
sudo umount -a
sudo mount -a
```

Of course, if you are just mounting it to the same point each time, you can name the folder you are mounting it to and change fstab to reflect it.

You can also use "**tune2fs -l**". Read about these commands at "**man command_name**".

---

### Post by graabein on 2008-06-09
Thanks for answering. I did both **sudo e2label /dev/sdc1 store** and **sudo tune2fs -L store /dev/sdc1** without any error messages or warnings and I did umount/mount between the two commands. Still the desktop icon and the Nautilus icon says *242.1 GB Media*. 

Here's my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=33b4c95a-1825-4d57-8bd5-2ab6e6f43483 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=024f689b-dde0-4fe4-944b-c4653ce0f932 /home           ext3    defaults        0       2
# /dev/sdc1
UUID=bdee2bc9-6e8a-443f-8015-d7dd25fa38b6 /media/store    ext3    defaults        0       2
# /dev/sdb1
UUID=A264B8B964B89191 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=C21C31B21C31A279 /media/xp       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=448efb02-95a6-4182-ae01-4577560a590c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```


[COLOR="DarkRed"]Update[/COLOR]: A restart did the trick! Thanks!

---

