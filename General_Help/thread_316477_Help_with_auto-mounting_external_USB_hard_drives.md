---
title: "Help with auto-mounting external USB hard drives"
date: 2006-12-10
forum: General Help
---

### Post by dreamer_cast on 2006-12-10
Hey guys, still here and still using ubuntu....just a question; I have 2 external USB drives that won't auto-mount at start-up.  I have to actually click on them in My Computer for them to mount.  I had to disable fsck checking at start-up because it constantly complaint about the file system not being correct for whatever reason.  Is it because of the last digit in fstab being "0" instead of "2"?  Could someone please let me know a way around this or perhaps a better way of accomplishing this?  Thanks in advance,

Dreamer

---

### Post by eriefisher on 2006-12-10
How are the drives formatted? What does the fstab say?

---

### Post by dreamer_cast on 2006-12-10
Wow, sorry about that, forgot to include my fstab...here it is....of course, sda, sdb1 are the ones in question



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc5 -- converted during upgrade to edgy
UUID=3520adc4-8721-4ea1-b04b-ec7839becad9 / ext3 defaults,errors=remount-ro 0 1
#/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda       /media/sda    ext3   defaults	0	0
#/dev/sdb1       /media/sdb1     ext3    defaults        0       0
# /dev/hdc6 -- converted during upgrade to edgy
UUID=d7b27ab9-5dad-434f-bfc8-f850cc54ee13 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

Dreamer

---

### Post by taurus on 2006-12-10
```

/dev/sda1  /media/sda   ext3  defaults  0  2
/dev/sdb1  /media/sdb1  ext3  defaults  0  2

```

---

### Post by dreamer_cast on 2006-12-11
Won't that turn back on the fsck check though?  Thanks for the help nonetheless

Dreamer

---

### Post by dreamer_cast on 2006-12-11
Anyone??

Dreamer

---

### Post by joe.webster on 2006-12-16
My understanding of automount is that you do not use fstab entries. I had problems with my usb flash drive and I fixed it by commenting out the fstab entries. 

More information here: [http://www.ubuntuforums.org/showthread.php?t=319897]("http://www.ubuntuforums.org/showthread.php?t=319897")

---

### Post by rlx01 on 2006-12-16
To get the mounted where you want you might have to ensure you have USB-storage support in the kernel.  I have two external USB storage devices and I just access them where they get mounted by default: /media/usbdisk

---

