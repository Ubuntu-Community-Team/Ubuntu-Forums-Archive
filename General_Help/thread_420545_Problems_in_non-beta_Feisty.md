---
title: "Problems in non-beta Feisty"
date: 2007-04-23
forum: General Help
---

### Post by revenge02 on 2007-04-23
I upgraded to Ubuntu Feisty yesterday (using the update-manager), and everything appeared to be fine. Until I tried to print something on my network printer. The only thing I can get through my network is the internet. Also, when I upgraded it mounted my Windows partition a second time, and when a try to unmount either of them, it gives me an error saying that it can't be unmounted because it has been mounted twice. When I try to unmount it in terminal, it appears that there is no unmount command. I was wondering if anyone has an idea on how to fix it, or how to go back to Edgy without re-installing. Thanks in advance.

---

### Post by ubu-for on 2007-04-23
> **revenge02 said:**
> ... or how to go back to Edgy without re-installing.

I don't think that it is possible to downgrade Ubuntu.

> **revenge02 said:**
> Also, when I upgraded it mounted my Windows partition a second time, and when a try to unmount either of them, it gives me an error saying that it can't be unmounted because it has been mounted twice. When I try to unmount it in terminal, it appears that there is no unmount command.

Go to "/etc/fstab" and check out your partitions. Maybe your Windows partition (ntfs) is mentioned twice.

---

### Post by jackmc on 2007-04-23
have you checked all of the printer settings? Mine took a while to get working as well..

---

### Post by revenge02 on 2007-04-23
> **ubu-for said:**
> 
Go to "/etc/fstab" and check out your partitions. Maybe your Windows partition (ntfs) is mentioned twice.
It's not mentioned twice.
This is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=220299c2-2e13-4bb3-bfba-bf22a8e3aa59 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=88699341-6c31-4022-a1e6-cecff92f0fd2 /boot           ext3    defaults        0       2
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
//192.168.0.1/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0 
```

---

### Post by ubu-for on 2007-04-24
This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5	/               ext3    defaults,errors=remount-ro 0       1
/dev/sda7	/home           ext3    defaults        0       2
/dev/sda1	/media/sda1	ntfs	defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2	/media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6	none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/home/user/Disk1 ext3	defaults	0	0
/dev/sdc1	/home/user/Disk2 ext3	defaults	0	0
```

Maybe it's because of your "ntfs-3g" entry?

---

### Post by revenge02 on 2007-04-24
For some reason it seems to have resolved itself. Now all I have to do is get my network printing to work. Thanks for the help ubu-for.
Edit - Okay, everything fixed itself... somehow.

---

