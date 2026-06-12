---
title: "automounting SATA hdd problem"
date: 2005-06-11
forum: General Help
---

### Post by fireedo on 2005-06-11
hi all....I have 2 hdd and I installed ubuntu on hdb and back up data on sda....
I have followed the instruction on ubuntuguide....but I always have to do this ----> "sudo mount -a" every time after I booting.....so any idea?

---

### Post by digby on 2005-06-11
To have a partition automounted at boot, you have to add it to your /etc/fstab file.

---

### Post by fireedo on 2005-06-11
[QUOTE=digby]To have a partition automounted at boot, you have to add it to your /etc/fstab file.[/QUOTE]
 Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    umask=0222      0       0


I have follow this way......and doesnt work!!!
I've change to suite my hdd condition........so anyidea

---

