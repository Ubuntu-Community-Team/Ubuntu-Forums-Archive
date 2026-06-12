---
title: "USB stick problem"
date: 2008-05-06
forum: General Help
---

### Post by interse on 2008-05-06
I formatted a USB stick to Ext. 2 using GParted.   When I tried to write to the stick, with Hardy Herron, I was denied access as the 'owner' was 'root'.  How do I switch to 'root' within Ubuntu so as to change the permissions on the USB stick.  I tried to switch user to root, but was rejected when switching to root.  Help.

THANKS TO ALL WHO REPLIED.  Solved with TeoBigusGeekus solution.

---

### Post by pro003 on 2008-05-06
from terminal:

```
sudo -s
``` type password...

also... 

```
gksu nautilus
``` type password...

and write to usb...

ps. why would you format your usb with ext2 anyway?

---

### Post by TeoBigusGeekus on 2008-05-06
Type 
```
sudo fdisk -l
```
to see how your stick is recognised - lets say /dev/sdc1


Then type
```
sudo chown -R yourusername /dev/sdc1
```

---

### Post by timcredible on 2008-05-06
ext2?  i would suggest re-formatting with ext3.  i've done this several times, usually leaving part of the stick as fat32 and part as ext3, never had a problem.

---

### Post by mali2297 on 2008-05-06
> **timcredible said:**
> ext2?  i would suggest re-formatting with ext3.  i've done this several times, usually leaving part of the stick as fat32 and part as ext3, never had a problem.

According to [Wikipedia]("http://en.wikipedia.org/wiki/Ext2"),
> 
ext2 is still recommended over journalized file systems for using in bootable USB sticks and likely other solid-state drives. ext2 shows less writing activity than ext3, as it does not need to write the journal. As the major aging factor of a Flash chip is the number of erase cycles, and as those happen frequently on writes, this increases the life span of the USB stick.

I don't know, but it sounds as a valid reason for using ext2.

---

