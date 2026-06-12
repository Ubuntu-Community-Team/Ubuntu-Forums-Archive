---
title: "cdrom problem"
date: 2006-11-14
forum: General Help
---

### Post by feest on 2006-11-14
hi, i have a problem with my cdrom drive, i recently purchased a new one (dvd writer) and now it doesn't think it's a cdrom it thinks it's a harddisk and it's mounted as hdb. since i have several apps installed that require to get data from the cdrom this gives a problem because they now try to get data from a not installed cd drive. i want my burner to be cdrom0 again, how do i do that?

---

### Post by feest on 2006-11-14
anyone?

---

### Post by mayonaise15 on 2006-11-14
can you post the contents of your /etc/fstab file please?

---

### Post by feest on 2006-11-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda4       /media/sda4               ext3    defaults,errors=remount-ro 0       1

*owyeah, the drive is now called hda*

---

### Post by mayonaise15 on 2006-11-15
Are you using a SCSI or SATA hard drive?  I'm just trying to get a picture of how all of your disk drives are hooked into your motherboard.

From looking at your /etc/fstab file I would guess that you have an SATA hard drive and you have plugged your DVD burner into the Primary IDE spot on your motherboard?  Do you have any other hard drives or CD-ROMs inside your case?  

The only guess that I have would be to check your jumper settings and make sure they are correct.  If all you have is the DVD burner and an SATA drive, I would make sure that your DVD burner's jumper is set to master.  If you want to, you could try moving the DVD's IDE cable to the Secondary IDE spot and edit your /etc/fstab file to say:
```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Best of luck to you.

---

### Post by feest on 2006-11-15
well your absolutely right,

i use a sata hdd
my dvd drive is plugged as master (not quite sure primairy or secondairy)
i have another hdd in the case (ide)

---

### Post by mayonaise15 on 2006-11-15
well, that might explain things.  I only see 2 devices in your list, hda and sda.  sda would be your boot device and hda is probably your other hard drive.  I would try changing that line in your /etc/fstab to what the code says in my last post.  If that doesn't work, try changing the line to read:
```
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
```
after you make changes to the /etc/fstab file go ahead and reboot.

Do you need access to your other hard drive?  If so, what prints out if you type:
```
sudo sfdisk -l
```

---

### Post by mistypotato on 2007-01-11
Don't ya just love it when you help someone and they're all over you until you solve their problem...then they don't even have the courtesy to say "thanks".

---

