---
title: "[SOLVED] How to make a harddrive mount at startup"
date: 2008-07-09
forum: General Help
---

### Post by Jimbo13 on 2008-07-09
I need to make my second drive automatically mount at start up or I can't stream media off of it.  Anyone know how to do that?

Thanks.

---

### Post by MasterXandrex on 2008-07-09
You will find the automount settings in /etc/fstab

here is an example:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=18F80CF9F80CD742 /media/vista    ntfs    defaults,umask=007,gid=46 0       1

```

Be sure to change the applicable fields -- you can find more info on these fields by using "man fstab" in the terminal

You can generate the UUID for your device by doing 
```

uuidgen /dev/sdc1

```
Where /dev/sdc1 is replaced by your device.

Xan

---

### Post by stchman on 2008-07-09
> **Jimbo13 said:**
> I need to make my second drive automatically mount at start up or I can't stream media off of it.  Anyone know how to do that?

Thanks.

What format is it?  NTFS, EXT3, FAT32, etc.?

---

### Post by Jimbo13 on 2008-07-09
This is my second drive I want to mount on startup.

[B]
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf1fcf1f

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 30400 244187968+ 7 HPFS/NTFS
[/B]

So do I put in **uuidgen /dev/Oxcflfcflf** in terminal for it to mount?




[I]
Not sure if it matters but this is my first HD with ubuntu installation.

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdad4f39a

Device Boot Start End Blocks Id System
/dev/sda1 * 1 421 3381651 7 HPFS/NTFS
/dev/sda2 422 7301 55263600 5 Extended
/dev/sda5 422 7116 53777556 83 Linux
/dev/sda6 7117 7301 1485981 82 Linux swap / Solaris[/I]

---

### Post by Jimbo13 on 2008-07-09
Any chance there is a short cut that just turns on all the drives all the time?

---

### Post by ktrnka on 2008-07-09
Make a directory in /media

> sudo mkdir /media/windows

Edit your fstab

> sudo nano /etc/fstab

add your partition to the bottom of the list:

> /dev/sdb1 /media/windows   ntfs-3g   defaults,locale=en_US.utf8 0 0 

hit ctrl-x 
then y

Then Reboot your computer

---

### Post by ktrnka on 2008-07-09
This should also give you plenty of information: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Jimbo13 on 2008-07-09
Thanks, it kicked right on after that.

---

### Post by ktrnka on 2008-07-09
Glad I could help.   :)

---

