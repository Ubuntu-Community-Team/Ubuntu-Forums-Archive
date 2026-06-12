---
title: "Ubuntu isn't using the main hard drive"
date: 2013-11-25
forum: General Help
---

### Post by tze.si on 2013-11-25
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   15G  2.1G  88% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           603M  928K  602M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  212K  1.5G   1% /run/shm
/dev/sda3       318G   18G  300G   6% /host
/dev/sde1       3.8G  3.5G  277M  93% /media/UUI
/dev/sda2       382G   58G  324G  15% /media/443404CC3404C342

```

The /host one is the one ubuntu should be using but after /dev/loop0 is used I get a "full disk error".
I obviously have done something wrong, I installed using wubi.

---

### Post by ccmiller12 on 2013-11-25
If you have installed using wubi, you should not have to mess with partitions,  it does that for you. If you still have access to your Windows OS, uninstall ubuntu via Control Panel. Then reinstall again. I'm not sure exactly what you did, but reinstalling might fix it. After reinstalling reboot and then go from there

---

### Post by coffeecat on 2013-11-25
With wubi, it doesn't matter how large the host partition is, the limiting factor is the size of your pseudo-partition in the C:\ubuntu\disks\root.disk file (or D:\ or E:\ depending on which Windows "drive" you installed wubi to). In your case it is 17G in size and was 88% full when you ran df. More here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by tze.si on 2013-11-25
Thank you for your responses @ccmiller12[COLOR=#000000]  and @coffeecat.
Is there any possibility I can fix this without reinstalling?
If not the steps I should follow are: 1. Log on Windows and delete the Ubuntu Partition 2. Re-create an Ubuntu partition 3. Boot an ubuntu usb/cd ?[/COLOR]

---

### Post by coffeecat on 2013-11-25
You might want to read through the link I posted. In this section:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

There is a link to this:

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

Wubi is only really intended as a tryout. If you want to replace it with a proper dual-boot, you can uninstall the wubi installation from inside Windows and setup a dual-boot by booting the live USB/CD. Before you do that, it's important to research what you wish to do if you haven't done it before. Here's a community documentation link which you might find useful:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Or others might be able to point you to a more comprehensive guide.

---

### Post by Mark Phelps on 2013-11-25
> 1. Log on Windows and delete the Ubuntu Partition

The /host entry means you installed INSIDE an existing Windows partition.  IF you delete that partition, you risk deleting Windows.

---

