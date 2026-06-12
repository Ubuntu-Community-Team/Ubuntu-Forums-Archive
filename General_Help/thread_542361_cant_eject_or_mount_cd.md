---
title: "cant eject or mount cd"
date: 2007-09-03
forum: General Help
---

### Post by atlfalcons866 on 2007-09-03
hi
i cant mount my new cd drive or eject. I have to restart my computer mount/eject.

---

### Post by DjBones on 2007-09-03
is it an external usb mounted cd drive or an internal drive?
although i believe ubuntu should do it automatically, you might have to edit the /etc/fstab file

a little more detail would help lol

---

### Post by strabes on 2007-09-03
What does the following command do?```
sudo eject /dev/cdrom
```

---

### Post by atlfalcons866 on 2007-09-03
jack@jack-desktop:~$ sudo eject /dev/cdrom
Password:
eject: unable to find or open device for: `/dev/cdrom'

here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ada3360a-c0cf-4b14-8602-2abe1ffaa109 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=0c356031-e2fd-45f6-a073-b1da75ec9b78 /home           ext3    defaults        0       2
# /dev/sda3
UUID=1615ca10-b91e-41b2-b67f-8a6ead7abad2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

it is an internal drive

---

### Post by Techno.Scavenger on 2007-09-03
Try sudo eject /media/cdrom0 
or sudo eject /dev/scd0

TechnoS

---

### Post by atlfalcons866 on 2007-09-04
still dosent work:(

---

### Post by DjBones on 2007-09-05
are you sure you have the hardware hooked up properly?
not too sound patronizing haha.. but it couldn't hurt to double check lol

---

### Post by atlfalcons866 on 2007-09-05
this weird but it fixes my problem.

 i have to leave a cd in there during boot. I also found my cd drive was the problem for my very slow boot. There is nothing wrong with the cd as i tried gusty gibbon and it worked so may be it was a kernel bug

---

### Post by Dungeon Keeper on 2007-09-08
Hi atlfalcons866,

Was with your same problem here using Ubuntu Feisty (amd64). I tried:
> sudo eject /dev/cdrom

Drive ejected after 1-2 minutes besides could not read disc. I leave the disc on it and reboot.

Ubuntu was taking too much time to load... So i press my drive's eject button when it starts to delay and the load's speed goes to normal. Ubuntu was able to open it after this. 

Should be some kind of problem with drive's load process cause that orange load bar was always stopping about 1 minute at the same spot. Hope somebody could figure what really happened so i post this information here. :confused:

My regards to all community.

---

### Post by atlfalcons866 on 2007-09-09
hi
I compiled the latest kernel and it seems like it is a kernel bug in 2.6.20.

---

### Post by pras29gb on 2007-10-11
hi all 
i have installed fiesty in my system and after the install 
the cd rom icon is not displayed in the "computer" . when i tried to mount it using /etc/fstab it does't worked please suggest me a solution.
do any one have the solution for this
mine is 
sempron 2400+
asus motherboard
with 512 mb ram

Is the same issue prevails with Gusty Gibbon  ?

---

