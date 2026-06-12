---
title: "Need help to mount hard drive and salvage data"
date: 2013-06-01
forum: General Help
---

### Post by s0563764 on 2013-06-01
Hi guys,

my mum's computer cannot load lubuntu on the computer anymore. The windows 7 partition is still alive though. Prior to this there was disk errors found when mounting, but I checked disk help and it seemed fine. Tried to use a live CD today to save some data, got this error:

> Error mounting /dev/sda7 at /media/lubuntu/3e4ffea7-a07a-4588-8678-2515c3e42029: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda7" "/media/lubuntu/3e4ffea7-a07a-4588-8678-2515c3e42029"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda7,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've tried a few ways to mount which lead to this: [HTML]mount: wrong fs type, bad option, bad superblock on /dev/sda,   missing codepage or helper program, or other error   In some cases useful info is found in syslog - try    dmesg | tail  or so[/HTML]

Is there anything I can do at this point? Or is all I can do is just wipe the comp and reinstall everything? Because this disk error happened before I think

---

### Post by UltraAnders on 2013-06-01
Use this command to make sure the UUID is correct and that it really is EXT4.
```
sudo blkid -c /dev/null -o list
```

You say you've tried a few ways to mount it, What are these?

Recovery Is Possible Live CD has saved me a few times, might be worth a punt.
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

---

### Post by s0563764 on 2013-06-01
> **UltraAnders said:**
> Use this command to make sure the UUID is correct and that it really is EXT4.
```
sudo blkid -c /dev/null -o list
```

You say you've tried a few ways to mount it, What are these?

Recovery Is Possible Live CD has saved me a few times, might be worth a punt.
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

Hi, thanks for the reply.

/dev/loop0 squashfs         /rofs          
/dev/sda1  ntfs    System   (not mounted)  08F02BD2F02BC4B2
/dev/sda2  ntfs    Windows  (not mounted)  B0262DB4262D7D0A
/dev/sda5  swap             <swap>         6a75cc6f-ba0f-46f2-a4a4-1233565c3c29
/dev/sda6  swap             <swap>         3291f237-d135-43f1-95ca-5fd12bdb52c5
/dev/sda7  ext4             (not mounted)  3e4ffea7-a07a-4588-8678-2515c3e42029
/dev/sr0   iso9660 Lubuntu 12.10 i386 /cdrom 
/dev/sdb1  ntfs    Seagate Expansion Drive /media/lubuntu/Seagate Expansion Drive 1070FBF070FBDA84

Its sda7 I can't mount. I've just tried to use programs from windows and live CD option to mount the drive[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by s0563764 on 2013-06-03
Used Live CD to check/fix drive. Seems to be a temp fix for now

---

