---
title: "mount / unmount external usb drive"
date: 2007-12-04
forum: General Help
---

### Post by Rippie on 2007-12-04
Help and explanation would be nice here boys..

Im having a 100GB external usb HDD that i've made 2 xfs partitions out of with GParted (stupid crashing program) but after i used that program it will mount the drives as DISK and DISK1

Well now i would like to have them to be called "private" and "software" so i did the following.

1. unmounted the drives that came after i made the two partitions with GParted
2. ran the following commands to mount my partition

```

sudo fdisk -l

sudo mkdir /media/private
sudo mount -t xfs /dev/sdb1 /media/private

sudo chmod -R 777 /media/private
sudo chown -R rippie /media/private

```

The above works great ..... but i cant right click on the drive and choose unmount, then i get this error with hal-mtab

Any ideas how to unmount them again ? or can i solve this problem a better way ?

I would be nice if i could just use the partitions GParted makes for me and rename them

---

### Post by Rippie on 2007-12-04
Doh ... now i cant delete the 2 directories ....

> rippie@riplaptop:/media$ sudo rmdir /media/private
rmdir: /media/private: Device or resource busy


Plz help guys

---

### Post by lswest on 2007-12-04
what exactly is the error from hal-mtab?  might help us figure it out.  Also you can just use QTParted instead of Gparted (i find it more stable)

[EDIT]
well if you want to permanently delete it you can use the command "rm -rf" and it should delete it whether it is busy or not
[/EDIT]

---

### Post by Rippie on 2007-12-04
> **lswest said:**
> what exactly is the error from hal-mtab?  might help us figure it out.  Also you can just use QTParted instead of Gparted (i find it more stable)

[EDIT]
well if you want to permanently delete it you can use the command "rm -rf" and it should delete it whether it is busy or not
[/EDIT]


HAL tells me that i cant unmount the drive by right clicking because its not in hal and i created the mount manual ..... but i cant get the message up now and i cant remove the directories ... give me this error now
> 
rippie@riplaptop:/media$ sudo rm -rf /media/private
rm: cannot lstat `/media/private': Input/output erro

---

### Post by lswest on 2007-12-04
hmm seems to be corrupted or unreadable (judging from the I/O error)...and for the unmounting...might be solved if you add it to the fstab file under /etc/fstab (i think that's where it is, on a windows box atm) and about the input/output error...i'm not really sure what that's all about...try with just "rm -r", see if you get the same error.

[EDIT]
was just re-reading your posts, stupid me.  You cant delete a mount point while it's in use, you'd have to unmount it first.  Probably rebooting would be best (unless its set to automatically mount, then you might want to disable that) and then reboot and delete the mount point, and try adding it to the /etc/fstab file.
[/EDIT]

---

### Post by Rippie on 2007-12-04
now i got them removed .... phew ....


so does anyknow a good way to rename a partition once its created ?

---

### Post by branque on 2007-12-04
what if you try...

sudo umount /dev/sdb1

---

### Post by lswest on 2007-12-04
like i said before, you could use QTParted to just remake the partition (not sure about the rename), or fdisk to remake it.  If you want to rename it (e.g. sda1 to Windows Drive or w/e) i've only ever done it in windows (i only ever have 2 drives, linux and windows, so i dont bother rename in linux) but i'm pretty sure you can do it in linux too.  Possibly apply an alias to it in the fdisk file.  tell me if any of my ideas work:P  also, umount without options implies its in the fstab file i believe.  [last edit (i think)] to change the drive name you have to change the name of the partition, so QT parted or fdisk should let you do it just fine[/last edit]

---

### Post by Rippie on 2007-12-04
Nice, solved the problem by create my new partitions and then followed this guide

[http://ubuntuswitch.wordpress.com/2007/06/04/howto-rename-a-xfs-filesystem-label-it/](http://ubuntuswitch.wordpress.com/2007/06/04/howto-rename-a-xfs-filesystem-label-it/)


THX guys for the quick help

---

