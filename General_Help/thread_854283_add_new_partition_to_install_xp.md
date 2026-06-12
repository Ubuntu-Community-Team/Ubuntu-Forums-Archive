---
title: "add new partition to install xp"
date: 2008-07-09
forum: General Help
---

### Post by scottybowl on 2008-07-09
hi, i have ubuntu installed on my laptop and now want to dual boot with XP

only problem is, it seems that every tutorial and example site out there is to show you how to create a dual boot when you're running windows

i've tried unmounting the sda partition using the partition editor but it gives me the error:

Could not unmount /dev/sda3
umount: /home: device is busy
umount: /home: device is busy

I assume all I need to do is unmount, resize or add a new partition which is FAT32/NTFS so that I can use this to install windows on without disrupting my ubuntu installation

Any ideas?

---

### Post by Elfy on 2008-07-09
You need to do it from either the buntu livecd or a bootable partition editor like partedmagic or gparted, as you found out you can't unmount the partition when you are running it.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

should help, you will need to reinstall grub after xp has finished installing.

You might find it necessary to unmount the swap if you use the buntu livecd -

```
sudo swapoff -a
```will do that for you.

Simply put 

resize exisitng partition
add new partition with unallocated space
install xp
reinstall grub

---

### Post by rraj.be on 2008-07-09
use Ubuntu live cd

in that go to terminal and type
```

sudo gparted
```

there you can resize and then you can reinstall.

Dont forget to reinstall your GRUB after windows installation

---

### Post by sancho panza on 2008-07-09
You should be able to do that by booting up using one of the partitioning Live CD. I dont remember the names of the latest ones off the top of my head. You should be able to boot up off those cds and then change your partitions, and then bootup using the XP and install.
Backup important files before messing with the partitions.

---

### Post by scottybowl on 2008-07-09
will all of these methods provide a GUI? I don't have the expertise to be messing around with partitions in the terminal

---

### Post by Elfy on 2008-07-09
not sure about partimage - never used it, but I don't think it's gui. But the partition editor in the buntu livecd gparted, which you can also get and use as a livecd in it's own right is, partedmagic is as well.

---

### Post by rraj.be on 2008-07-09
> **forestpixie said:**
> not sure about partimage - never used it, but I don't think it's gui. But the partition editor in the buntu livecd gparted, which you can also get and use as a livecd in it's own right is, partedmagic is as well.


Extremely sorry.

I want to mention gparted but made small mistake due to another busy work.

To The OP: Extremely sorry

---

