---
title: "Dvd mounted for other user logged"
date: 2008-04-26
forum: General Help
---

### Post by tuberculo on 2008-04-26
When I insert a DVD in the driver and there is another user logged, I can open the disk, but I can't use Brasero or umount. Also, this message appears:
> mount: block device /dev/scd0 is write-protected, mounting read-only

mount: /dev/scd0 already mounted or /media/cdrom0 busy

mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0



The mount command gives me this:

> /dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ANOTHERUSER)



My fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0729e10c-4069-4f49-b279-41954b39e1ed /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=0cff29ec-4605-41e5-bc3f-09f37c50993d /home           ext3    defaults        0       2
# /dev/sda1
UUID=DC4084D34084B634 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=3b5598ef-ed20-42a1-bc26-fa817127b9cf /media/sda6     reiserfs defaults        0       2
# /dev/sda7
UUID=86571ab8-73cb-45c5-bbef-8f6397d75166 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I can't find a similar problem in the forum.

---

### Post by ryanhaigh on 2008-04-26
Have you got the system setup so that when a dvd is inserted it starts playing or opens nautilus or anything? If the dvd is being accessed by a program you probably wont be able to unmount it although you could try using the terminal and doing
```
sudo umount /media/cdrom0
```

To change whether an app opens the dvd go to system>prefs>removable drive and media and uncheck the box there, although this is a per user setting so you might have some trouble. Perhaps there is an associated gconf-key you could set as mandatory.

---

### Post by ryanhaigh on 2008-04-26
Have you got the system setup so that when a dvd is inserted it starts playing or opens nautilus or anything? If the dvd is being accessed by a program you probably wont be able to unmount it although you could try using the terminal and doing
```
sudo umount /media/cdrom0
```

To change whether an app opens the dvd go to system>prefs>removable drive and media and uncheck the box there, although this is a per user setting so you might have some trouble. Perhaps there is an associated gconf-key you could set as mandatory.

---

### Post by tuberculo on 2008-04-26
> **ryanhaigh said:**
> Have you got the system setup so that when a dvd is inserted it starts playing or opens nautilus or anything? If the dvd is being accessed by a program you probably wont be able to unmount it although you could try using the terminal and doing
```
sudo umount /media/cdrom0
```

To change whether an app opens the dvd go to system>prefs>removable drive and media and uncheck the box there, although this is a per user setting so you might have some trouble. Perhaps there is an associated gconf-key you could set as mandatory.

There is no DVD or CD on system>prefs>removable drive and media.

---

### Post by tuberculo on 2008-04-26
The strange thing is that the other user is the one who can umount the disk.

---

