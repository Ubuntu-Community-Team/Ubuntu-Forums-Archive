---
title: "I need root privileges to access /media"
date: 2007-05-17
forum: General Help
---

### Post by iAlta on 2007-05-17
I think I accidentally somehow maybe made it so that I need root privileges to access /media. So now I can't access my portable drives, and my legacy NTFS drive.

---

### Post by taurus on 2007-05-17
How do you mount your ntfs drives?  Do you mount them by hand or do they get mounted automatically?

---

### Post by iAlta on 2007-05-18
Are you asking what I did?

It kinda mounted itself, and I just activated it  through the GUI... And then clicked to quick on a pop up window... :/

EDIT: I changed to mount point of the NTFS drive to /mnt and now I don't need root to access the /media directory, but now I need root to get to /mnt.
At least I know where the problem is...

---

### Post by bung33 on 2007-05-18
I wonder if it has anything to do with the permissions of the specific folder. Post the output of...

```
ls -l /
```

Check the permissions for media and mnt. You may need to change them...

---

### Post by taurus on 2007-05-18
```
sudo fdisk -l
df -h
```

---

### Post by iAlta on 2007-05-18
```
drwxr-xr-x   4 root root  4096 2007-05-18 16:34 media
dr-x------   1 root root 16384 2007-05-09 17:48 mnt

```
```
Disk /dev/hda: 20.4 GB, 20485785600 bytes
16 heads, 63 sectors/track, 39693 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          62       31216+  83  Linux
/dev/hda2              63        7812     3906000   83  Linux
/dev/hda3            7813       37754    15090768   83  Linux
/dev/hda4           37755       39692      976752   82  Linux swap / Solaris

Disk /dev/hdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        5004    40194598+   7  HPFS/NTFS

```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             3.7G  3.7G     0 100% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  116K  252M   1% /proc/bus/usb
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1              30M   19M  9.6M  66% /boot
/dev/hda3              15G  3.5G   10G  26% /home
/dev/hdc1              39G   36G  2.5G  94% /mnt
/dev/hdb              3.7G  3.7G     0 100% /media/cdrom0
/dev/hdb              3.7G  3.7G     0 100% /media/cdrom0

```

---

### Post by taurus on 2007-05-18
Can you post your /etc/fstab also?

```
cat /etc/fstab
```

---

### Post by iAlta on 2007-05-19
sorry, but I just reinstalled the whole damn thing, because I had other problems too and it was easier and faster to just reinstall it.

---

