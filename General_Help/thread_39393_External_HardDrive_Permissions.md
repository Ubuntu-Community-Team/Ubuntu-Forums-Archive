---
title: "External HardDrive Permissions"
date: 2005-06-04
forum: General Help
---

### Post by xbilly on 2005-06-04
I want to change the permissions to my External hard drive so that i can write to it. How do I do this?

---

### Post by dave9191 on 2005-06-04
```
sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
```

you'll just want to change that to your drive location and the mount point you want. That should give read/write access for all users. 

Dave

---

### Post by xbilly on 2005-06-04
Sorry I didnt quite follow. The address to my harddirve, currently is /media/ieee1394disk

How do it add that to the terminal code you gave me?

---

### Post by dave9191 on 2005-06-04
sudo mount /dev/xxxx /media/ieee1394disk -t vfat -o umask=000

where /dev/xxx is the location of the drive. and /media/ieee1394disk is the mount point. Im guessing that the xxx will be somehting like sda1 or sdb1.

---

### Post by xbilly on 2005-06-04
I get a message saying:

mount: /dev/sda1 already mounted or /media/ieee1394disk busy
mount: according to mtab, /dev/sda1 is already mounted on /media/ieee1394disk

---

### Post by dave9191 on 2005-06-04
You cant mount a drive that already mounted. Thats the command you need to use to mount it. If its already mounted, then unmount it first.

umount /dev/xxx

if that complains that the drive is busy you can wait a bit and try again or you can do a 

umount -l /dev/xxx

---

### Post by xbilly on 2005-06-04
Okay I unmounted it as far as I know but now I get this after putting this in again (sudo mount /dev/sda1 /media/ieee1394disk -t vfat -o umask=000):

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by dave9191 on 2005-06-04
It might not be sda1 then. And if its not a fat formated drive, replace the vfat with whatever file system you are using.

---

### Post by xbilly on 2005-06-04
That seemed to have mounted it... but I still can't change the permissions because it says it is "read-only"

---

### Post by xbilly on 2005-06-04
it says i am not the owner

---

### Post by dave9191 on 2005-06-05
I dont know then :( Thats how I mount my drive and it works fine. Try wrighting stuff to it as root instead. so open a root file managment window. 'sudo nautilus' ( or however its spelt).

---

### Post by m0biu5 on 2005-06-05
When I copied stuff from my Windows internal hard drive to Ubuntu last weekend, it didn't like the user/permissions either. I used a Root Terminal to chown to myself and change the permissions to what they needed to be for me to write to the files. Is there any way you can do that to the files on the external hard drive?

---

