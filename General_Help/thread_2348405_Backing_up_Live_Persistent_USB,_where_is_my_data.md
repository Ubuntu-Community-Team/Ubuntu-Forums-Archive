---
title: "Backing up Live Persistent USB, where is my data?"
date: 2017-01-03
forum: General Help
---

### Post by ubuntini2 on 2017-01-03
Hi
If you're not actually booting off a Live Persistent USB, is it still possible to back up your data?

By data, I mean any text or script files saved to your Home folder.

Where is this located on the USB?

---

### Post by Habitual on 2017-01-03
Hello eco_bach :D

---

### Post by ppnman on 2017-01-03
You NEED live persistent USB in order to restore data, otherwise you can't save any data ON the usb,only on the hdd,and that files will belongs to root.

---

### Post by sudodus on 2017-01-03
I assume that you have a persistent live drive, and that you have run it in persistent mode. Then you could have saved personal files and tweaks in your home directory. You could also have installed some program package and maybe done some global tweaks, that are saved, but not in the home directory.

A standard Ubuntu persistent live system stores the persistent data in a file named casper-rw or in a partition labeled casper-rw. That is where you have the data to be backed up.

You may make things a little more advanced, and create a second partition for persistence, a file named home-rw or a partition labeled home-rw. In that case you find the data to be backed up in both 'casper-rw' and 'home-rw'.

And you can perform this backup, when booted live-only (without persistence). The data are there. One example is the backup and restore system of mkusb described at the following link,

[mkusb/persistent#Backup_and_restore_of_persistent_overlay_data](https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data)

---

### Post by C.S.Cameron on 2017-01-03
If  the persistent drive was made using Startup Disk Creator, (Pre 16.04), UNetbootin, Universal, Rufus, etc it will have a casper-rw file on the root of the drive, (FAT32)
I have had good luck simply copying that file to backup media, (hard drive or second USB). This can be done from Windows or while booted from a second Live USB or DVD.

If the drive was made using mkusb or another grub2 type installer, it will have a casper-rw partition which is ext2, 3 or 4, (not visible to Windows).
This persistent partition can be cloned using gparted, Clonezilla or dd, while booted from a second Live USB or DVD.

---

### Post by efflandt on 2017-01-04
You can loop mount the casper-rw file if you plug the live persistent USB device into another computer running Linux. The USB device auto mounts in /media/your_username/its_UUID:```
efflandt@XPS-8100-1404:~$ ls /media/efflandt/
93B8-DE6B

efflandt@XPS-8100-1404:~$ sudo mount /media/efflandt/93B8-DE6B/casper-rw /mnt -o loop
[sudo] password for efflandt: 

efflandt@XPS-8100-1404:~$ ls -l /mnt
total 28
-rw-r--r--  1 root root   109 Jan  4 11:53 format
drwx------  2 root root 16384 Jan  4 11:03 lost+found
drwxr-xr-x 11 root root  4096 Jan  4 11:53 upper
drwxr-xr-x  3 root root  4096 Jan  4 11:53 work

efflandt@XPS-8100-1404:~$ ls -l /mnt/upper
total 36
drwxr-xr-x  3 root root 4096 Aug  3 10:57 boot
drwxr-xr-x  2 root root 4096 Jan  4 11:53 cdrom
drwxr-xr-x 13 root root 4096 Jan  4 11:56 etc
drwxr-xr-x  3 root root 4096 Jan  4 11:53 home
drwxr-xr-x  2 root root 4096 Jan  4 11:53 media
drwxr-xr-x  2 root root 4096 Jan  4 11:53 rofs
drwxrwxrwt  3 root root 4096 Jan  4 11:53 tmp
drwxr-xr-x  5 root root 4096 Aug  3 10:25 usr
drwxr-xr-x  6 root root 4096 Aug  3 10:57 var

efflandt@XPS-8100-1404:~$ ls -l /mnt/upper/home/ubuntu
total 32
drwxr-xr-x 2 999 999 4096 Jan  4 11:54 Desktop
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Documents
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Downloads
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Music
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Pictures
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Public
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Templates
drwxr-xr-x 2 999 999 4096 Jan  4 11:53 Videos
```

---

