---
title: "NTFS signature is missing."
date: 2019-05-05
forum: General Help
---

### Post by nick2learn on 2019-05-05
I'm running Ubuntu 16.04, full install.
I have an SD card with some gopro footage that won't open (no SD card will open on my ubuntu laptop in the slot) I can see the files and open on the mac. It's a new SD. I also put the SD card into a USB reader and plugged it into the laptop and got the following
I searched for solution to the following error:
****
Error mounting /dev/sdc1 at /media/nick/6363-3933: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdc1" "/media/nick/6363-3933"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
*****
and ran this:
***** opened terminal
nick@MSI:~$ sudo ntfsfix /dev/sdc1
[sudo] password for nick: 
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
nick@MSI:~$ ^C
nick@MSI:~$ 
*****
Can anyone help please? :)

This is what I got with the SD card in the SD slot:
***** opened terminal
nick@MSI:~$ sudo ntfsfix /dev/mmcblk0p1
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
nick@MSI:~$ 
*****

---

### Post by Impavidus on 2019-05-05
Like most larger sd cards, it has an exfat filesystem. Exfat is not ntfs, so ntfsfix is not going to help (and can fix only simple issues anyway). Support for exfat isn't installed by default, but you can install it from the repositories:```
sudo apt install exfat-fuse
```or use a different interface to the package manager.

You may wish the exfat utilities as well, to create, check or label exfat filesystems:```
sudo apt install exfat-utils
```

---

### Post by The Cog on 2019-05-05
See this link for a good explanation and solution: [https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/)

Edit: Beaten by Impavidus. That's what happens when you go to make a slice of toast between reading and answering a post.

---

### Post by nick2learn on 2019-05-05
awesome! worked straight away!!! Thank you so much! :)

---

