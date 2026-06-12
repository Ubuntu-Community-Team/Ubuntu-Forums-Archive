---
title: "partitions not detected"
date: 2005-08-02
forum: General Help
---

### Post by limonada on 2005-08-02
I am new to linux and i don't know where exactly to post this question.I hope that somebody can help me though.So here it goes: i have installed ubuntu but it seems that excepting the installation partition,the other partitions are not available.They are FAT32.So what's wrong?

---

### Post by frodon on 2005-08-02
Well

you need after the install to edit your fstab file, this file specify the partitions to be mounted on startup.

1) First find the name of your FAT32 partition(s) : ```
/sbin/fdisk -l /dev/hda
``` try with hdb , hdc or hdd if your partition is (are) not in hda. Then remember the name of your partition (hda1 for exemple)
2) Create a directory where you want to mount your partition(s) generally in /mnt or /media, i give you an exemple if you want to mount your partition in /mnt/disk : ```
cd /mnt
sudo mkdir disk
```
3) Open your fstab file : ```
sudo gedit /etc/fstab
```and add a line for each partition like that : ```
/dev/hda1	/mnt/disk	vfat	rw,user,exec,umask=0		0	0
``` hda1 is the name of the partition and /mnt/disk is the directory where your partition will be mounted.
4) reboot

EDIT : modified as black_hole_sun suggested it  ;-)

---

### Post by black hole sun on 2005-08-02
[QUOTE=frodon]Well

you need after the install to edit your fstab file, this file specify the partitions to be mounted on startup.

1) First find the name of your FAT32 partition(s) : ```
/sbin/fdisk -l /dev/hdb
``` try with hdc and hdd if your partition are not in hdb. Then remember the name of your partition (hdd1 for exemple)
2) Create a directory where you want to mount your partition(s) generally in /mnt or /media, i give you an exemple if you want to mount your partition in /mnt/disk : ```
cd /mnt
sudo mkdir disk
```
3) Open your fstab file : ```
sudo gedit /etc/fstab
```and add a line for each partition like that : ```
/dev/hdd1	/mnt/disk	vfat	rw,user,exec,umask=0		0	0
``` hdd1 is the name of the partition and /mnt/disk is the directory where your partition will be mounted.
4) reboot[/QUOTE]
 frodon; unless he has two harddrives, why are you suggesting hdb and not hda which is what 99% of us have? Why would you suggest hdc (typically the cdrom) or hdb? Don't make it harder than it has to be.

lemonade ( ;) ); probably you should use "hda" and "hda<number>" in the above commands, of course according to your own partition layout.

---

### Post by frodon on 2005-08-02
[QUOTE=black hole sun]frodon; unless he has two harddrives, why are you suggesting hdb and not hda which is what 99% of us have? Why would you suggest hdc (typically the cdrom) or hdb? Don't make it harder than it has to be.

lemonade ( ;) ); probably you should use "hda" and "hda<number>" in the above commands, of course according to your own partition layout.[/QUOTE]
lol you're right  :smile: 
But I already find persons with a disk in hdb and I don't know why but often I think that everybody have 2 disks !
Maybe it's easier to test all  ... hda, hdb, hdc, hdd so you're sure to find your partition (in my mind it is  :roll: ).

---

### Post by limonada on 2005-08-03
Actually...I have 2 disks  :smile:

---

### Post by limonada on 2005-08-03
Thanks to both of you for your help.It worked  :smile:

---

