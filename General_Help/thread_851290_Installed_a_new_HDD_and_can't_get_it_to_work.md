---
title: "Installed a new HDD and can't get it to work"
date: 2008-07-06
forum: General Help
---

### Post by IceDigger on 2008-07-06
I just installed a second 640GB hard drive in my computer and I cant seem to write anything to it.  I formated it with gparted to ext3.

I don't know how to use a command line.

---

### Post by cariboo on 2008-07-06
In a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

Paste the output in your next post, So that we can help you out.

Jim

---

### Post by Elfy on 2008-07-06
You will need to mount it to use it, make a folder and edit fstab to include it so it mounts with boot

Find it's UUID with 
```
sudo blkid
```

make folder
```
sudo mkdir /media/nameofdisc
```

backup and edit fstab
```
sudo cp /etc/fstab /etc/fstab.0607
gksudo gedit /etc/fstab
```

Add this to end - put UUID from blkid in drectly after UUID=

> #newdisc
UUID= /media/nameofdisc default 0 2

mount with this to check
```
sudo mount -a
```

---

### Post by mc4man on 2008-07-06
If your using 8.04 and _don't want/need the drive to auto mount at boot_ ( in other words just mount and unmount as needed with full permissions ) it's become very easy to do with just the mouse. All you need to do is grant yourself 'Explicit Authorization to mount filesystems from internal drives'. The easiest way is to find the partition(s) in places (either visible there or in removable media or computer), double click on it and you should get a popup to authenticate. enter your password and ck. the remember ... box. Otherwise you can do the same from system -> admin -> authorizations -> storage -> mount filesystem from internal drives -> explicit authorizations -> grant, choose your user name ect.
After that you can mount and unmount as wanted with the mouse

---

