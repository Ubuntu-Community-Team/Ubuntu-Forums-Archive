---
title: "Permission denied [Resolved]"
date: 2007-04-24
forum: General Help
---

### Post by jmtjet on 2007-04-24
How do I set permissions to access /etc/fstab. I'm trying to mount my external harddrive in Fiesty Fawn. Fiesty sees the drive but I'm unable to mount it, even as root-permission denied- the drive is formated FAT 32. Any help will be greatly appreciated.

---

### Post by taurus on 2007-04-24
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by aysiu on 2007-04-24
Two great readings for you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jmtjet on 2007-04-24
Thanks for your replies. My external drive is recorded as sda1 in fdisk. How would I go about mounting it? 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  L

---

### Post by taurus on 2007-04-24
```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sda1 /media/windows -o iocharset=utf8,umask=000
df -h
```

By the way, is your swap working at all?

```
free
```

---

### Post by jmtjet on 2007-04-24
Thanks for your reply. Here's what I get after I the first set of commands;
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.5G   31G   8% /
varrun               1014M  108K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  124K 1014M   1% /proc/bus/usb
udev                 1014M  124K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              75G  132M   75G   1% /fat_files
/dev/sda1              75G  132M   75G   1% /media/wind

and the free command yields;
         total       used       free     shared    buffers     cached
Mem:       2076144     371536    1704608          0      10056     222068
-/+ buffers/cache:     139412    1936732
Swap:      1646620          0    164662

---

### Post by aysiu on 2007-04-24
That's weird.

/dev/sda1 appears to be mounted in two different directories: ```
/dev/sda1 75G 132M 75G 1% **/fat_files**
/dev/sda1 75G 132M 75G 1% **/media/wind**
``` Is that even possible?

---

### Post by jmtjet on 2007-04-24
> /dev/sda1 appears to be mounted in two different directories:

I have no idea. :) I've been trying since last night to get this drive mounted up. I've followed more than one set of directions. :)

---

### Post by taurus on 2007-04-24
What does your /etc/fstab look like then?

```
cat /etc/fstab
```

---

### Post by jmtjet on 2007-04-24
Thanks for the help. Here's the cat /etc/stab output;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3b79c3b2-e033-4e05-af1e-4fed23b97109 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=33ec2057-2fcf-489f-9c08-e2b39914399f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /fat_files vfat iocharset=utf8,umask=000 0 0
jeff@jeff-desktop:~$

---

### Post by taurus on 2007-04-24
Just reboot and look at this output again.

```
df -h
```
Your /dev/sda1 will be mounted to /fat_files, as instructed in /etc/fstab.

---

### Post by jmtjet on 2007-04-24
the command; df -h yielded:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.5G   31G   8% /
varrun               1014M  108K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  128K 1014M   1% /proc/bus/usb
udev                 1014M  128K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              75G  132M   75G   1% /fat_files

Now, how to I access the drive. It doesn't seem to be listed anywhere? Thanks for your help.

---

### Post by jmtjet on 2007-04-24
Update: Got it! Finally. :)  I created an icon on the workspace to the Fat_files folder. Now I'm able a access the files on my external drive. Thanks all.

---

