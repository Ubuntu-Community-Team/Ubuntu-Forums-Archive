---
title: "How to edit files while using live cd?"
date: 2008-05-06
forum: General Help
---

### Post by one4house on 2008-05-06
I have a GRUB install that I need to edit the menu.lst file for.  I am accessing the file from the live CD because I cannot get this install of Ubuntu to load up.  Every time I try and save the edited file it says I do not have permission to save the file.  Is there a way around this?

I have tried mounting the drive in OS X and it will not mount the drive.  It does see it as a Linux drive but will not allow mounting.  The other problem is that my Vista install does not see the drive at all.

PUZZLED

---

### Post by one4house on 2008-05-06
When in SUDO GRUB is there a way to get into some kind of edit mode that will allow me to change the menu.lst file?

---

### Post by TeoBigusGeekus on 2008-05-06
You could install ifs driver in vista to see your linux partition (provided it's ext2 or ext3):
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by one4house on 2008-05-06
Thanks, but it does not see it.  Thanks for trying.

---

### Post by warp99 on 2008-05-06
> **one4house said:**
> I have a GRUB install that I need to edit the menu.lst file for.  I am accessing the file from the live CD because I cannot get this install of Ubuntu to load up.  Every time I try and save the edited file it says I do not have permission to save the file.  Is there a way around this?

I have tried mounting the drive in OS X and it will not mount the drive.  It does see it as a Linux drive but will not allow mounting.  The other problem is that my Vista install does not see the drive at all.

PUZZLED

Boot up your LiveCD, open a terminal and do the following:

```
sudo mkdir /media/tmp
```
then mount the drive:
```
sudo mount /dev/<name_of_device> /media/tmp
```
change directory to the mounted device:
```
  cd /media/tmp/boot/grub
```
then edit your menu.lst
```
 sudo nano menu.lst
```
 then 'crtl+o' to save and 'crtl+x' to exit. Now issue a 'sudo reboot' to get you back to your normal boot session. Remember to change the <name_of_device> to you partition.

Edit:

For some unknown reason if you don't have write permissions to the 'menu.lst' file then in the '/boot/grub/' directory run the following:
```
 sudo chmod 644 menu.lst
```

---

### Post by bodhi.zazen on 2008-05-06
If you wish to use gedit, start it with gksu

```
gksu gedit /path/to/menu.lst
```

@warp99: this is what /mnt is for, temp mounts.

so you can :

sudo mount /dev/<device> /mnt

sudo nano /mnt/boot/grub/menu.lst

Saves on the typing

Also, you really should not change permissions of system files.

---

### Post by warp99 on 2008-05-06
> **bodhi.zazen said:**
> 
@warp99: this is what /mnt is for, temp mounts.

Some older versions  of Ubuntu don't have a /mnt directory. OP did not specify which version he had.

> 
Also, you really should not change permissions of system files.
If he can't write to it because it look like this:
```
-r--r--r-- 1 root root   4866 2008-04-22 03:49 menu.lst
```
What do you expect him to do? I admit after checking that it should be 'chmod 644 menu.lst', which is read/write owner only.

---

### Post by one4house on 2008-05-06
Can someone give me an example of of a name for device? I tried hd1,2 and hd1 and it just says "cant find dev/hd1/media/tmp in etc/fstab or etc/mtab"

---

### Post by one4house on 2008-05-06
> 

Edit:

For some unknown reason if you don't have write permissions to the 'menu.lst' file then in the '/boot/grub/' directory run the following:
```
 sudo chmod 644 menu.lst
```

How do I get to that directory in a certain drive?  I just cant seem to find it in Terminal.

---

### Post by bodhi.zazen on 2008-05-06
For an overview of linux partitions see here :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

To list your partitions use fdisk

```
sudo fdisk -l
```

If can identity the partition you need to mount we can mount it.

---

### Post by one4house on 2008-05-06
I want to mount the Linux partition:

He fdisk list my 2 drives

sda <-----Vista
sdb <Linux and Mac

sda is listed 

sda1
sda2 (Actual Vista Patition)
sda3
sda4

partitions 1 and 4 are for acer's recovery tool. 3 is just a storage patition.

sdb is listed as

sdb1 Linux swap partition
sdb2 (it list this as unknown in linux) but it is Mac OS X
sdb3 Linux

---

### Post by one4house on 2008-05-06
bump

---

### Post by bodhi.zazen on 2008-05-06
sudo mount /dev/sdb3 /mnt

gksu gedit /mnt/boot/grub/menu.lst

---

