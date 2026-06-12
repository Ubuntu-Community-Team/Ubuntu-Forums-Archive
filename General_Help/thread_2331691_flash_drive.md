---
title: "flash drive"
date: 2016-07-24
forum: General Help
---

### Post by TheTinyt1 on 2016-07-24
I know t hat this is simple but, i can not correct the problem.  I am using ubuntu 16,94 64 bit and am trying to fix a flash drive. The drive somehow has become withe protected and I am unable to correct the problem. I am trying to format the device to a fat 32 system and can not seem to get it to format. can  any one please help me with this.

many thanks in advance...

---

### Post by &amp;KyT$0P# on 2016-07-24
How are you trying to format the disk?

Please post here a screenshot of GParted showing this flash drive, with View > Device Info selected.
If you don't already have GParted installed, run this command in a Terminal to install it:
```
sudo apt-get install gparted
```

---

### Post by TheTinyt1 on 2016-07-24
yes I am using gparted and this is the error message: Cant write to /dev/sdl, because it is opened read-only.

I have no idea as to how this has happened but is shows this error. I did not think that you could make these things read only/\.

---

### Post by Bucky Ball on 2016-07-24
Can you right click and unmount it in Gparted? Can you unmount it in a file manager? If so, do so and then right click on the partition in Gparted and 'delete'. 

You might also try switching the machine off, reboot and straight to Gparted. If you don't click the USB dongle it shouldn't mount from a fresh start as a FAT32 partition.

---

### Post by kurt18947 on 2016-07-24
What I've seen is not your problem but I'll mention it anyway. Gparted as it comes with Ubuntu-Gnome 16.04 64 bit may have 'issues' and be giving incorrect information. When I work with hard drive partitions I get a message about conflicting sector sizes. Gparted from a 14.04 live USB works as expected. If you have 'Disks' (actually gnome-disks) installed you might try that and see if your USB appears locked there as well.

---

### Post by &amp;KyT$0P# on 2016-07-24
> **TheTinyt1 said:**
> yes I am using gparted and this is the error message: Cant write to /dev/sdl, because it is opened read-only.

Thanks but can you please post a screenshot of the GParted window when View > Device Info is checked and the flash drive is selected?  This won't require triggering the error message; just would like to know what it looks like to just viewing the device.

---

### Post by Bucky Ball on 2016-07-24
Also, what is the drive formatted as now? If it is EXT*, then find its mountpoint (open in a file manager and check the path in the pathbar), for instance /media/sdl, and:

```
sudo chown -R username:username /media/sdl
```

... where 'username' is your username and /media/sdl is the correct path to the mount point.

Incidentally, /dev/sdl refers to the entire USB dongle, not a partition. You can't format the USB, you create a partition on it and format that to whatever filesystem type you're after.

---

### Post by &amp;KyT$0P# on 2016-07-24
> **Bucky Ball said:**
> Incidentally, /dev/sdl refers to the entire USB dongle, not a partition. You can't format the USB, you create a partition on it and format that to whatever filesystem type you're after.
Unless the device's partition table type is "loop", where it can only have a single partition, that is referenced by like /dev/sdl

---

### Post by TheTinyt1 on 2016-07-25
I did as you suggested and rebooted and then deleted the partition. then I formated it. 

It seems to have worded.

Thank you for you assistance in this matter...

Hope you have a very blessed day...

---

### Post by Bucky Ball on 2016-07-25
Good news and thanks for marking as solved. ;)

---

