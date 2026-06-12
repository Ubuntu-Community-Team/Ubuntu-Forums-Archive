---
title: "Gold Lock Icons on Folders in Tree"
date: 2007-05-19
forum: General Help
---

### Post by DarkW0lf on 2007-05-19
I have some Gold Icons appearing on my folders when I view them in the file manager.
Attempting to create files or folders in them result in an error telling me I don't have permission.

My external hard drive was rw before as one NTFS but when I reformatted it to two Ext3 it is now ro ?
I am not sure what happened, if I did anything or what to check, the USB drive doesn't appear in fstab.
And media/hda2 is actually not there any more I deleted my WinXP partition, why is it still there ?

What should I look at for info?

FSTAB output:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ce43630d-f69d-4f52-af42-d6bd7b104d97 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=3a090b1f-9676-4557-92fb-a882764acb68 /home           ext3    defaults        0       2
# /dev/hda2
UUID=A2CC84B0CC847FF1 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=1506bdf9-14a3-4d63-87c5-36dc2285be4f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by vtel57 on 2007-05-19
Your fstab is **not** a dynamic file, meaning it doesn't change itself when you make changes to your hardware. It must be edited manually to add/remove items.

The gold padlocks on directories and files that you're seeing means that Root access is required. These items belong to Root. They're not accessible to the users.

---

### Post by DarkW0lf on 2007-05-20
Yes I can understand that but why is the USB drive now root only when it was user with FAT formatting ?
(It wasn't NTFS, oops)

I got the same thing for the Filesystem that wasn't there before too I think.
In any case, I need user access to the external hard drive to store my data.
Root access for the backup partition is ok because SimpleBackup runs as root anyway.
But it's just the mount point that read-only right ? If I were to change /media/usbdisk would that be the correct thing to do or would that still leave the drive ro.

It is sometimes a liitle wierd with Linux having both the device and a mount point.
Where does ubuntu keep the config for the usb drives, I can read fstab for the other drives and see how they are mounted but where to I look for USB drives they aren't listed in fstab.

---

### Post by vtel57 on 2007-05-20
I'm not that familiar with USB devices in Linux. However, I can tell you that ALL devices in Linux are viewed by the operating system (the kernel) as files. When you "mount" a device, what you're actually doing is accessing the corresponding file for that device. 

Which device in your above fstab is this USB drive? If you've made **any** changes to the device (formatting, changing device location, etc.), you'll have to edit your fstab. The fstab is a configuration file that allows regular users to mount devices. 

If you leave "ro" in the entry in fstab, the device will **only** mount as read only.

We're on the outer edges of my knowledge here, DarkWolf. Hopefully, others will pop in here with some suggestions for you.

Luck!

~Eric

---

### Post by DarkW0lf on 2007-05-26
It's not listed as far as I can tell.
I know it should be displayed as a SCSI drive (sda) but I am not seeing any sda entries in fstab.
I don't know where else a USB device maybe listed.

SInce it was never listed in fstab I don't know where to edit in order to mount rw

---

