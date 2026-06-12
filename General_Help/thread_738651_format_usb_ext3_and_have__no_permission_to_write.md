---
title: "format usb ext3 and have  no permission to write"
date: 2008-03-28
forum: General Help
---

### Post by El Viejo Lobo on 2008-03-28
I got my USB hard disk formated by using the how to I found here: [http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
This is my backup driver and now I can not write into it, see the screen-shot attached.
I tried to change proprieties and it dose not work see second Screen-shot.
Help is needed, Please.

---

### Post by ibuclaw on 2008-03-29
Try this while your external drive is inserted.
Type in a terminal:
```

ls /dev/sdc*
#something like this will be printed.
sdc  sdc1  sdc5
#take note of the highest number pointer.
#then type this in to unmount and remount with read/write capabilities

pumount /dev/sdc5
pmount -w /dev/sdc5

```

That should give you temporary relief for the session/while the device is mounted.

Although I don't recommend it, you can look into adding an "fstab" location for your external devices.

Regards

---

### Post by El Viejo Lobo on 2008-03-29
This is what I got by using " ls /dev/sdc* "

lobo@lobo-laptop:~$ ls /dev/sdc*
ls: /dev/sdc*: No such file or directory
lobo@lobo-laptop:~$

---

### Post by ibuclaw on 2008-03-29
How many hard drives do you have?

It may be being mounted on sdb then.

Sorry, I have two hard drisk drives and am used to my flash sticks being mounted on /dev/sdc or /dev/sdd.


But until you figure out where the pointer to your external storage device is being placed.

I'll just run you through what pmount is:

pmount is essentially the command "mount", except you can use it without sudo or root permissions; or for that matter, any detail on the device you are mounting.
the extension "-w" means that you want to mount the device with read/write capabilities. "-r" with just read.

Knowing this, pumount is self explanitory.

Regards

---

### Post by El Viejo Lobo on 2008-03-29
No problem here are names of the disks.

The laptop disk is

/dev/sda1   *           1       11977    96205221   83  Linux
/dev/sda2           11978       12161     1477980    5  Extended
/dev/sda5           11978       12161     1477948+  82  Linux swap / Solaris

The USB disk is:
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d3aec79

---

### Post by ibuclaw on 2008-03-29
Cool!

It was just a matter of replacing **c** with **b** then!

```

ls /dev/sdb*
**sdb sdb1**
pumount /dev/sdb1
pmount /dev/sdb1 /media/path

```

Again, this is was only supposed to be a temporary work around.

If you want it permanent look up your /etc/fstab file and make an entry for it.

Something like:
```
 /dev/sdb1 /media/**mydrive**    msdos,vfat,fat    defaults,umask=007,gid=46 0       1 
```


Regards

---

### Post by El Viejo Lobo on 2008-03-29
Sorry, it is not working, as you can see in the attached screenshot.

---

