---
title: "ext3 partition mount impossible"
date: 2005-10-18
forum: General Help
---

### Post by frederictoulouse on 2005-10-18
I have 2 hard disks on my computer, hda with unbuntu hoary and hdb with the last Ubuntu Breezy Badger :


# fdisk -l

Disque /dev/hda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1        1702    13671283+  83  Linux
/dev/hda2            1703        1945     1951897+  82  Linux swap / Solaris
/dev/hda3            1946        9729    62524980    5  Extended
/dev/hda5            1946        4377    19535008+  83  Linux
/dev/hda6            4378        9729    42989908+  83  Linux

Disque /dev/hdb: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1               1        1824    14651248+  83  Linux
/dev/hdb2            1825        9729    63496912+   5  Extended
/dev/hdb5            1825        4256    19535008+  83  Linux
/dev/hdb6            4257        4499     1951866   82  Linux swap / Solaris
/dev/hdb7            4500        9729    42009943+  83  Linux


When I use Ubuntu Breezy Badger, I can't mount any partition of hda :( 
# mount -t ext3 /dev/hdb7 /mnt/
mount: /dev/hdb7 est déjà monté ou /mnt/ est occupé

nothing is mounted on /mnt and I obtain the same error with any directory and any hdb partition.

according to mtab, hdb7 is not mounted :
# more /etc/mtab 
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda6 /archives ext3 rw 0 0
/dev/hda5 /home ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0


and my fstab is :
# more /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /archives       ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I use the new kernel 2.6.13 so I suppose that I need to tune something in the kernel, but what ? Another possiblity, in Ubuntu Breezy Badger is there an automount somewhere ? where are the hard disks mounted ?

may thanks for your answers :D

---

### Post by frederictoulouse on 2005-10-18
sorry, hoary is on hdb and badger on hda ;)

---

### Post by SilentCacophony on 2005-10-18
> When I use Ubuntu Breezy Badger, I can't mount any partition of hda
# mount -t ext3 /dev/hdb7 /mnt/
mount: /dev/hdb7 est d&#233;j&#224; mont&#233; ou /mnt/ est occup&#233;

nothing is mounted on /mnt and I obtain the same error with any directory and any hdb partition.

I don't think that mounting directly onto /mnt/ is good. Maybe try this:

sudo mkdir /media/hdb7
sudo mount /dev/hdb7 /media/hdb7/ -t ext3

---

### Post by frederictoulouse on 2005-10-18
# mkdir /media/hdb7
# mount /dev/hdb7 /media/hdb7/ -t ext3
mount: /dev/hdb7 est déjà monté ou /media/hdb7/ est occupé

the problem is the same with any directory :confused:

---

### Post by paddyg on 2005-10-18
[QUOTE=frederictoulouse]
and my fstab is :
# more /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /archives       ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/QUOTE]

I don't see any mention of any hdb mount points in your fstab. I've got two hds as well, but my fstab records them all.
Have you tried adding something like
/dev/hdb7  /media/hdb7  ext3  noauto,users  0 2  ?
Hope it helps.

---

### Post by Zwack on 2005-10-18
[QUOTE=frederictoulouse]# mkdir /media/hdb7
# mount /dev/hdb7 /media/hdb7/ -t ext3
mount: /dev/hdb7 est déjà monté ou /media/hdb7/ est occupé

the problem is the same with any directory :confused:[/QUOTE]

Interesting...

The error states that the filesystem is already mounted or the directory is in use.  

You don't need the trailing / on the mount point name but it works either way (I've just tested)...

Given that the mount command doesn't show that the directory IS mounted, and the subdirectory is not actually in use (it shouldn't be if you've just created it,  fuser -cux /media/hdb7 would answer that for certain) then I would wonder about permissions.  Are you sure that /dev/hdb7 is correct?

Can you check /proc/mounts as it can be more up to date than /etc/mtab?

Given that ext3 can be mounted as ext2, can you try that?  If that works then I would guess that these are actually ext2 and not ext3 filesystems.

Z.

---

### Post by frederictoulouse on 2005-10-19
Yes it is a very strange problem that I have never seen before. The problem is the same with ext2 and ext3. My opinion is that there is something to tune in the kernel or a process to kill but I dont know what ...
It is not a permission since I tried that as root.

more /proc/mounts 
rootfs / rootfs rw 0 0
/dev2/root2 / ext3 rw 0 0
proc /proc proc rw,nodiratime 0 0
sysfs /sys sysfs rw 0 0
/dev2/root2 /dev/.static/dev ext3 rw 0 0
none /dev tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda6 /archives ext3 rw 0 0
/dev/hda5 /home ext3 rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0

 ls -l  /mnt
total 4
drwxr-xr-x  2 root root 4096 2005-10-18 15:05 disk1

---

### Post by EricZapletal on 2005-10-19
Hi,

have you try to stop the 'evms' service ?

This service has something to do with the management of the partitions and it may interfere with user 'mount' ..

sudo /etc/init.d/evms stop

and then try to mount other partitions

EZ

---

### Post by frederictoulouse on 2005-10-19
# /etc/init.d/evms stop
# mount -t ext2 /dev/hdb7 /mnt/
mount: /dev/hdb7 est déjà monté ou /mnt/ est occupé

:confused: 

thank you for your answer but evms has no effect...

---

### Post by EricZapletal on 2005-10-19
ok,

maybe you have to uninstall the 'evms' package :

[http://www.ussg.iu.edu/hypermail/linux/kernel/0408.3/0141.html]("http://www.ussg.iu.edu/hypermail/linux/kernel/0408.3/0141.html")

I had the same problem once and it really helped me.

I thought that stopping the service was sufficient, that's why I suggested it to you in my last post but obviously I was wrong.

EZ

---

### Post by frederictoulouse on 2005-10-19
Congratulation !!!!! :D 

You found the good solution : after removing EVMS it is now possible to mount another hard disk on my file system !!!! :KS 

Thank you very much ;)

---

