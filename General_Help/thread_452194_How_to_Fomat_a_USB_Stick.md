---
title: "How to Fomat a USB Stick ?"
date: 2007-05-23
forum: General Help
---

### Post by Palko on 2007-05-23
Hello,

I'm using Ubuntu 7.04 - the Feisty Fawn

anyway I want to format my USB flash drive clean, not get shifted trash bin on the drive it self.

please help,

thank you,

Palko, :)

---

### Post by deeZee on 2007-05-23
Take a look at this post [http://ubuntuforums.org/showthread.php?t=424518&highlight=install+on+flash+drive](http://ubuntuforums.org/showthread.php?t=424518&highlight=install+on+flash+drive)  I've not tried this personally, but the link within it gives instructions for formatting a flash drive.  Hope it helps.:)

---

### Post by Palko on 2007-05-23
no no, I just want to format my USB stick, :(   

you know how in windows you go right click/ format,

---

### Post by coxy on 2007-05-23
I think what deeZee means is the link will contain instructions on formatting a USB flash drive as this would be part of the process when using USB as your installation media. Have a look at the link and it will be one of the first steps.

---

### Post by deeZee on 2007-05-23
Yes, I understand that.  [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)  Look at steps 3 through 9.  That may be what you're looking for.

---

### Post by vanadium on 2007-05-23
Formatting is not a daily task and should not be in the right-click menu. In Ubuntu, it isn't fortunately.

1) Have your USB inserted. Determine where your USB is mounted:

* Right-click the icon, properties, volume tab: take note of the mount point. It might be, for example, /media/USB
* Open a command prompt, type

```

mount

```

One of the lines (probably the last one) will contain the mount point. The start of the line geves you the device name, e.g.

```

/dev/sdb1 on /media/USB type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

```

In this example, the device is /dev/sdb1

2. Reformat the drive. Suppose we are reformatting in vfat (Windows FAT32 system)

In a command prompt, type

sudo umount /dev/sdb1
sudo mkfs -t vfat /dev/sdb1
sudo eject /dev/sdb1

Instead of vfat, you fmight substitute ext2, ext3, msdos (FAT16) or any other valid file system. Now take out the USB and reinsert it, so that it gets mounted again.

For compatibility, I recommend to use vfat for USB sticks. If yours is already formatted in vfat, then don bother with reformatting. Just erase all files that are on it.

---

### Post by Palko on 2007-05-23
Are you guys serous, I thought ubuntu was Linux for humans?

What if formatting is your daily task? 

I really didn't want to type commands to just to clean simply my flash drive?

surly there must be a faster way for the average 'on the go' person to format his or her sick.

---

### Post by iggyboy on 2007-05-23
There are GUI to perform your required task, below are step-by-step guide may be off help to you:

1. Plug-In your USB Disk Drive to your system, When your see the USB Disk Drive icon in your Desktop, right click at the icon and click **UNMOUNT VOLUME**. (Do NOT physically remove your USB Disk Drive yet)

2. Goto **SYSTEM > ADMINISTRATION > GNOME PARTITION EDITOR***

3. On the right hand side of the Gnome Partition Editor window, you will see a pull down menu. Choose your USB DISK. (if you don't have any SCSI or SATA Hard Disk then most probably */device/sda*, but please be sure that you choose the right disk drive other wise you will end-up formating your hard disk)

4. Once you have choose the correct item from the menu list; a list will appear at below window. (most probably only one line, unless you have partition your USB Disk Drive to more then one partitions).

5. Right click at the desired item from the available list item, then goto **FORMAT TO > FAT32**

6. Finally click **APPLY** from the top menu icon.

That's all for GUI Steps :)

*
Well... Let say you don't have **Gnome Partition Editor** installed. Then to install it follow below steps:

Click at **APPLICATION** and chose **ADD/REMOVE**, then goto **SYSTEM TOOLS** and tick **GNOME PARTITION EDITOR** and **APPLY**.


please let me know if you got any problem following above guide :)

Regards :)

---

### Post by eentonig on 2007-05-23
> **Palko said:**
> Are you guys serous, I thought ubuntu was Linux for humans?

What if formatting is your daily task? 

I really didn't want to type commands to just to clean simply my flash drive?

surly there must be a faster way for the average 'on the go' person to format his or her sick.

:D I can' t help to wonder who's job it would be to format flash drives every day?

Anyway.

1. The CLI explanation you were given, might not be the most Userfriendly at first sight. But it's definitly the most foolproof way of helping you over the internet. With CLI, you can most of the time suffice with copy&paste. No misunderstandings in interpretation.
2. If you really don't want tp type in commands to ... (whatever stupid task), I'm afraid you'll get disappointed a lot whil using linux. Allthough GUI are develloping fast. The CLI is most of the time the most flexible, easiest and fastest way of working. Heck, if one told me a year ago I would do most of my image processing on a CLI, I would have died laughing. But yet, about 80% of my graphics work is now done this way. And it saves me a lot of time.

3. To answer your question "What if formatting is your daily task? " You write (Or ask someone to do it for you) a simple script (~batch file) that automates the repetitive steps. Two days later, you'll agree that CLI is much faster. ;)

---

