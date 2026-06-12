---
title: "access data on windows in KDE [Resolved]"
date: 2007-01-06
forum: General Help
---

### Post by Russty of Oz on 2007-01-06
I have done a search for how to access data on my windows partition but can only find threads doing the opposite.  In gnome I get an icon on the desktop for hda 1 but I prefer to use KDE, so how  do I get the hda 1 icon on my KDE desktop instead of having to change sessions all the time.

---

### Post by aysiu on 2007-01-06
Mounting is actually pretty desktop environment-independent.

It's defined by your /etc/fstab file, and you can modify that following these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If it's already mounted, what you can do is right-click on the desktop in KDE, go to Desktop > Behavior > Devices and select to show mounted drives on the desktop.

---

### Post by Russty of Oz on 2007-01-06
When I do the sudo fdisk -l bit it says** /dev/sda 2**

does it matter that it is sda rather than hda?

---

### Post by aysiu on 2007-01-06
> **Russty of Oz said:**
> When I do the sudo fdisk -l bit it says** /dev/sda 2**

does it matter that it is sda rather than hda?
No.

Have you tried my suggestion?

And if that didn't work, can you post the output of **all** of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Russty of Oz on 2007-01-06
I did try the desktop thing but nothing showed up.

here are the outputs 

russty@russty-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833       17508   126070560    7  HPFS/NTFS
/dev/sda3           17509       25424    59844960   83  Linux
/dev/sda4           25425       25841     3152520   82  Linux swap / Solaris
russty@russty-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              57G  5.7G   48G  11% /
varrun                760M   96K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb             10M  204K  9.9M   2% /proc/bus/usb
udev                   10M  204K  9.9M   2% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   20M  740M   3% /lib/modules/2.6.17-10-386/volatile
/dev/sda1             6.0G  5.1G  986M  84% /media/sda1
/dev/sda2             121G   75G   46G  62% /media/sda2
russty@russty-desktop:~$cat /etc/fstab

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833       17508   126070560    7  HPFS/NTFS
/dev/sda3           17509       25424    59844960   83  Linux
/dev/sda4           25425       25841     3152520   82  Linux swap / Solaris
russty@russty-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              57G  5.7G   48G  11% /
varrun                760M   96K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb             10M  204K  9.9M   2% /proc/bus/usb
udev                   10M  204K  9.9M   2% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   20M  740M   3% /lib/modules/2.6.17-10-386/volatile
/dev/sda1             6.0G  5.1G  986M  84% /media/sda1
/dev/sda2             121G   75G   46G  62% /media/sda2
russty@russty-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7aa19b76-4e2b-4d73-9aec-56da90dff9a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=429A-C07D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1ACAA7414B3134A5 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=325d3062-aa61-47ab-8eb5-aaf077f0081f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
russty@russty-desktop:~$

---

### Post by aysiu on 2007-01-06
Well, your Windows drive is mounted to /media/sda2, so it's weird that it's not showing up on your desktop, even after doing that "show mounted drives" thing.

The other option, of course, is to symlink it: ```
sudo ln -s /media/sda2 ~/Desktop/windows
``` Then it'll appear on your desktop as a folder called *windows*. You can, of course, have that name be anything--*sda2*, for example: ```
sudo ln -s /media/sda2 ~/Desktop/sda2
```

---

### Post by Russty of Oz on 2007-01-06
YES! :D   That now shows up as a folder called Windows.

Thank you very much, now I can just work from KDE.  I find that I rarely boot into windows now days, I find now that Ubuntu can do almost everything, BETTER!  

Russty.:KS

---

