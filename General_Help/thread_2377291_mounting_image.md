---
title: "mounting image"
date: 2017-11-11
forum: General Help
---

### Post by rikyki on 2017-11-11
Hello, i have used testdisk to try to recover some files from an SSD so now i have an image.dd in my Documents folder. I've search how to do and i have followed that:
[https://ubuntuforums.org/showthread.php?t=1697571&p=10508025#post10508025](https://ubuntuforums.org/showthread.php?t=1697571&p=10508025#post10508025)

But i'm a beginner with Ubuntu and i don't know what to do now:
> NAME@NAME-System-Product-Name:~$ sudo mkdir /mnt/disk_image
[sudo] password for NAME: 
NAME@NAME-System-Product-Name:~$ sudo mount -o loop -t auto /home/NAME/Documents/image.dd /mnt/disk_image
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
NAME@NAME-System-Product-Name:~$ 


Can someone help me please?

---

### Post by Holger_Gehrke on 2017-11-11
Now you can access the disk-image on the path you mounted it to. In the Directory '/mnt/disk_image' you should now see the content of the filesystem if you open it in your filemanager and be able to copy the files you want to recover to your disk.
The messages the 'mount' command gave are purely informational.

Holger

---

### Post by rikyki on 2017-11-11
Ho ! All my files are there ! Thank you for the help.

---

