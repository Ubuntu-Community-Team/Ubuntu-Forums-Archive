---
title: "Gparted"
date: 2007-03-11
forum: General Help
---

### Post by Elena678 on 2007-03-11
hi, i would like to plit my hard disk in 2 parts, so i can put one one part the system, and one the other part my files, so that when i need to reïnstall my computer, that i am not losing everything,

I was tying out gparted to fix it, but when i start it up, and select a partition, i have no options in the partition scroll down menu, (only unmount, partition flags and infromation)

so i can't recise, or can't make a new partition :S

thanks for the help

greetings

---

### Post by bernied on 2007-03-11
1. Are you running gparted on a disk that you are using at the time? This would be a bad idea and gparted might stop you  from editing the disk (but it should give you a message 'disk is mounted')
2. Are you running gparted as root (adiministrator) user? You will not have the rights to change partitions without running as root.

Be very careful when resizing partitions - this can go wrong and there is the risk that you will lose access to your data. So find a way to make a backup if there is anything there that you value.

I suggest that you only run gparted from a live-cd, if you are changing the hard disk where your operating system is. If you use the Ubuntu live-cd, then run it like this:
```
gksu gparted &
```or run it from the menu (that should be configured to run as root).

---

### Post by viper on 2007-03-11
Download the latest live cd iso for gparted from here.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Elena678 on 2007-03-11
can i burn that iso file also on a usb stick, so that i can boot from the usb device (i never did this, so i don´t know if it can, and how it works)

thanks for all the info :)

---

### Post by viper on 2007-03-11
at the same link you should find a link called "live usb"

---

### Post by bernied on 2007-03-11
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by viper on 2007-03-11
> **bernied said:**
> [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

Good point :)

---

### Post by Elena678 on 2007-03-11
hi, well, i made a new partition, a ext3, name is  /dev/hda3 witout a flag.

but i don't see it when i start up ubuntu, i tink it is becouse it is unmounted, but i don't know how to mount.

thx

---

### Post by Elena678 on 2007-03-11
i founded this, but this is not working very well for me :S

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bernied on 2007-03-11
Where is it going wrong?

Can you show me the output from```
mount
```and```
cat /etc/fstab
```and```
sudo fdisk -l
```

---

### Post by Elena678 on 2007-03-11
output of mount
```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=elena)

```

outupt of cat /etc/fstab [COLOR="Red"]i think when i change this it is going fold, becose i did not find a save option[/COLOR]
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5b455350-67db-4679-964b-a0b69104f6f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=20bf490f-f7ea-4351-b036-7e872f8b5554 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

output of sudo fdisk -l
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3187    25599546   83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda3            3188        4676    11960392+  83  Linux
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

thanks m greetings

---

### Post by bernied on 2007-03-11
OK, so you need to change the /etc/fstab file, that guide tells you what to do. When you hit Ctrl-X to get out of nano, it should ask you if you want to save the file, just hit the 'y' key and Enter to save and exit.
Then go ahead and do the rest.
Post any error messages here.

---

### Post by Elena678 on 2007-03-11
i tink it is working now, but do you know why the map in storage is called as lost+found


thanks for the big help.

greetings

---

### Post by bernied on 2007-03-11
Apparently the 'lost&found' directory is the place where files are put if there is a problem with the hard disk and the filesystem get s corrupted. So if you lose some files, look there for them.

Have fun
Bernie

---

