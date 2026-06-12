---
title: "Transfer to another disk"
date: 2005-04-29
forum: General Help
---

### Post by xMaximex on 2005-04-29
Hi,

I'd like to transfer my installation to another disk .. presently it is on /dev/hdb1 but I want to transfer if on /dev/hda1 .. how can I proceed ?

---

### Post by defkewl on 2005-04-29
Try changing the harddisk to master

---

### Post by cutOff on 2005-04-29
[QUOTE=xMaximex]Hi,

I'd like to transfer my installation to another disk .. presently it is on /dev/hdb1 but I want to transfer if on /dev/hda1 .. how can I proceed ?[/QUOTE]
Not be sure but editing your /etc/fstab and changing the corresponding entries.

Regards

---

### Post by darkcoder on 2005-04-29
Have you copied the data or not.

This guide while limited to /home can give you an idea of how to do it.

[Partitioning in action: Moving /home](http://www-106.ibm.com/developerworks/library/l-partplan.html)

---

### Post by darkcoder on 2005-04-29
Since you are moving the whole drive, IMHO your best way is to boot from a Live CD like the Ubuntu Hoary Live CD, or Knoppix, or a simple and small Gentoo install-x86-minimal.iso (56 MB).  

1. Boot from the Live/Rescue CD.
2. Make the partitions needed on the new hard disk.
3. Mount the drives (and give them easy names like /mnt/hda or /mnt/old) 
4. Copy the files from  one drive to the other. 
```
cp -Rp /mnt/old/* /mnt/new/
``` 
Important, do not leave the -Rp.  That copies Recursively and keeps Permisions.
5.  If the disk will be placed on another position on the IDE chain (secondary instead of primary),  you have to made the changes to /etc/fstab, and /boot/grub/menu.lst
6. Turn off your PC.
7. Put the new drive in place
8. Reboot and cross your fingers.

---

