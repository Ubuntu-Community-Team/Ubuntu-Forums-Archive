---
title: "Can someone post a &quot;clean&quot; fstab file?"
date: 2006-12-07
forum: General Help
---

### Post by darco on 2006-12-07
I overwrote my original fstab and was wondering if someone could post an orignal fstab for me. I have Edgy and overrode it w/an fstab file from my Fedora Core distro. Doh!
thxs
dr

---

### Post by aidanr on 2006-12-07
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dd958b0e-6248-492f-bd22-a38b47a86512 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=651a380e-edc5-4922-ba2f-54c41d623d42 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/mnt/maxtor 	ext3 	defaults,errors=remount-ro 	0 	1
thats mine, of course you'll have to change the /dev/whatever with your own and as far as i know you can replace the UUID with /dev/whatever, i'm not sure what the command is to get the UUID of a partition

---

### Post by darco on 2006-12-07
This is my current fstab file that I copied from a previous FC6 system.
I had to rem out the BOOT as Ubuntu did not recognize it, thats when I realized my mistake. I dont get any other errors on boot up.
When I run a mount -a , I get a 
mount: sysfs already mounted or /sys busy
mount: according to mtab, /sys is already mounted on /sys

Is this fstab file ok?


/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
#LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0
/dev/hdb5               /mnt/win                auto rw,users,umask=000 1 0              
/dev/hdb7               /mnt/xp                 auto rw,users,umask=000 1 0
/dev/hdd                /media/cdrom            auto    pamconsole,exec,noauto,managed 0 0
//192.168.15.100/downloads    /mnt/downloads smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777   0    0
//192.168.15.104/share       /mnt/share      smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777   0    0

---

### Post by taurus on 2006-12-07
You need to specify where your / and swap are, something like

```

/dev/hda1   /   ext3   defaults,errors=remount-ro    0   1
/dev/hda5   none   swap   sw   0   0

```
And if you are not sure what partitions are your / and swap, run this command from a prompt to find out.

```
sudo fdisk -l
```

---

### Post by darco on 2006-12-07
here is the output of fdisk -l.....so at this point what do I need to do?



Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           2       24321   195350400    f  W95 Ext'd (LBA)
/dev/hdb5               2       11643    93514333+   b  W95 FAT32
/dev/hdb6           11644       12709     8562613+  83  Linux
/dev/hdb7           12710       24321    93273358+   b  W95 FAT32

---

### Post by taurus on 2006-12-07
Well, your /etc/fstab probably should look something like this then!

```

/dev/hda1  /  ext3  defaults,errors=remount-ro   0  1
/dev/hda5  none  swap  sw  0  0
/dev/hdb5 /mnt/win auto rw,users,umask=000 1 0
/dev/hdb7 /mnt/xp auto rw,users,umask=000 1 0
/dev/hdd /media/cdrom auto pamconsole,exec,noauto,managed 0 0
//192.168.15.100/downloads /mnt/downloads smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
//192.168.15.104/share /mnt/share smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```

---

### Post by darco on 2006-12-07
Ok , that seemed to work...thxs

dr

---

### Post by taurus on 2006-12-07
> **darco said:**
> Ok , that seemed to work...thxs

dr

Good.

---

### Post by rbmorse on 2006-12-07
> **aidanr said:**
> i'm not sure what the command is to get the UUID of a partition

You can find them in /dev/disk/by-uuid

---

### Post by darco on 2006-12-08
After booting up with this "new" file, my system was slow as a dog..I reverted back to my FC6 fstab file and its back to a fast system. It must be the swap file?

dr

---

