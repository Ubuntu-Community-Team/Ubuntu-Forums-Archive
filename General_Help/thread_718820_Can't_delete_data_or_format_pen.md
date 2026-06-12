---
title: "Can't delete data or format pen"
date: 2008-03-08
forum: General Help
---

### Post by ruialexbarbosa on 2008-03-08
Hi,

please help! I have a 4gb pen that was working fine, and now I can't save anything in it or delete from it. It will seem that it copied the info but when I take it of and put it back again, nothing has changed.

I tried formating it with gparted and it won't work (even after ejecting it).

How can I just reformat absolutely everything?

Thanks

---

### Post by ruialexbarbosa on 2008-03-09
I'm sure someone has an idea... Please?

---

### Post by PmDematagoda on 2008-03-09
What filesystem does the pendrive use? Also do you get any errors when trying to format it?

---

### Post by ruialexbarbosa on 2008-03-09
Ok, thanks for your answer. This is what happens:

I uncheck the boxes for auto mounting the disk, then open gparted (sudo gparted) and chose my pen which apears in dev/sda1.

I get a warning sign in GPARTED saying open /dev/sda1/ no such file or directory.

It shows the parition as being a fat16 3.89GB.

I delete the partition it says "all operations completed succesfully"

I create a fat32 partition, it says "all operations completed succesfully", I click CLOSE and in GPARTED the partition appears as FAT16 again.

When I mount the pen, all of the files are still there... Weird...

Can you help?

Thanks

---

### Post by PmDematagoda on 2008-03-09
Could you please post the output of:-
```
cat /etc/mtab
```
when the pen drive is plugged in.

---

### Post by ruialexbarbosa on 2008-03-09
This is what comes up:

alex@casa:~$ cat /etc/mtab
/dev/hda7 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/hda5 /fat32 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hda1 /windows ntfs rw,umask=222,utf8 0 0
usbfs /proc/bus/usb usbfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb /media/PEN vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
alex@casa:~$

---

