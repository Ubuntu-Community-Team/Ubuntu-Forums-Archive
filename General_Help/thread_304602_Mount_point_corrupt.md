---
title: "Mount point corrupt"
date: 2006-11-22
forum: General Help
---

### Post by PhoenixAndy on 2006-11-22
So, when I reboot, I get the following in my /media

```

astanford@osiris:/media$ ls -l
total 40
lrwxrwxrwx 1 root root      6 2006-09-03 09:07 cdrom -> cdrom0
drwxr-xr-x 2 root root   4096 2006-09-03 09:07 cdrom0
?--------- ? ?    ?         ?                ? downloads
drwxr-xr-x 2 root root   4096 2006-11-21 19:56 downloads2
lrwxrwxrwx 1 root root      7 2006-09-03 09:07 floppy -> floppy0
drwxr-xr-x 2 root root   4096 2006-09-03 09:07 floppy0
drwxr-xr-x 7 root root  16384 1970-01-01 01:00 hda1
dr-x------ 1 root root   4096 2006-11-21 19:12 hda5
drwxr-xr-x 5 root root   4096 2006-10-07 11:24 hda6
drwxrwsr-x 5 root staff  4096 2005-03-15 23:52 hdb4

```

downloads *should* be the mount point for a samba share on my fileserver, as shown in my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       none            swap    sw              0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=f0761bd7-feec-4eaf-abc3-f44bc0da8f5d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=1C89-3214 /media/hda1 vfat defaults 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=44E0FDDAE0FDD1E2 /media/hda5 ntfs defaults 0 0
# /dev/hda6 -- converted during upgrade to edgy
UUID=58f0e718-d8e1-4b4a-8e1a-adc07485b5b7 /media/hda6 ext3 defaults 0 2
# /dev/hdb4 -- converted during upgrade to edgy
UUID=068d8e4b-ac87-4eaf-8472-5df57ba4a66f /media/hdb4 ext3 defaults 0 2
# /dev/hdb3 -- converted during upgrade to edgy
UUID=93045059-1aef-4a1a-a049-c3e480c592c0 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//ra/downloads  /media/downloads        smbfs   username=*******,password=******,uid=*****,gid=****     0       2

```

It only happens after a reboot, and only started happening recently. It also appeared that my swap wasn't being activated, so I added the old-style line at the top.

Any ideas on how to stop this happening?

---

### Post by PhoenixAndy on 2006-11-22
It's also feasible that this problem is a direct result of trying to hibernate the computer.

I know the swap issues didn't start until after I attempted to hibernate, and have a feeling that this problem started at around the same time.

---

