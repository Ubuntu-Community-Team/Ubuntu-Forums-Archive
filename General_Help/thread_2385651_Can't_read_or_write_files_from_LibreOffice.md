---
title: "Can't read or write files from LibreOffice"
date: 2018-02-22
forum: General Help
---

### Post by pogona on 2018-02-22
From yesterday, whenever I try to load a file from certain drives into LibreOffice I get the message "Access to /media/***/xxx.yyy was denied.", and a similar message appears if I try to save a file from LO. Permissions are set for read/write access by the user, and other programs (e.g. Text Editor) can open and save the same files to the same locations.

Not all drives are affected. LO can read/write from usb drives. It may be coincidence, but the affected drives have NTFS file systems: those with ext4 or FAT32 file systems seem to be OK.

I can work around the problem by moving the required files to an unaffected drive (or to the desktop) and then load them into LO, and reverse the process when I want to save them. But that's not a long-term solution.

Not being a geek, I am at a loss to know where to turn. Any helpful suggestions welcome!

System: Ubuntu 17.04
LibreOffice: Version: 5.4.5.1 / Build ID: 1:5.4.5-0ubuntu0.17.10.1

---

### Post by vasa1 on 2018-02-22
Please see [https://ubuntuforums.org/showthread.php?t=2385549](https://ubuntuforums.org/showthread.php?t=2385549)
and [https://askubuntu.com/questions/1008880/libreoffice-5-4-5-1-gets-access-denied-on-nfs-mounted-filesystem](https://askubuntu.com/questions/1008880/libreoffice-5-4-5-1-gets-access-denied-on-nfs-mounted-filesystem)

---

### Post by pogona on 2018-02-23
I've just upgraded to LibreOffice 6.0.1.1, and all is sweet.

---

