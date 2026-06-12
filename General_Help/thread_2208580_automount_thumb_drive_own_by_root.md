---
title: "automount thumb drive own by root"
date: 2014-03-01
forum: General Help
---

### Post by fire-fly2 on 2014-03-01
Hi 
I am able to automount my thumb drive on "Ubuntu 12.04.4 " server as  ordinary user ( non root). However after mounting the owner was root.   drwxr-xr-x 4 root root 2048 Jan  1  1970 PP

  
How can change the ownership ?

  The automout file  auto.usb was as below.
#
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# Details may be found in the autofs(5) manpage

#cd        -fstype=iso9660,ro,nosuid,nodev    :/dev/cdrom

# the following entries are samples to pique your imagination
#linux        -ro,soft,intr        ftp.example.org:/pub/linux
#boot        -fstype=ext2        :/dev/hda1
#floppy        -fstype=auto        :/dev/fd0
#floppy        -fstype=ext2        :/dev/fd0
#e2floppy    -fstype=ext2        :/dev/fd0
#jaz        -fstype=ext2        :/dev/sdc1
#removable    -fstype=ext2        :/dev/hddA
PP -fstype=vfat :/dev/sdi1

Please help.
Thanks

---

### Post by varunendra on 2014-03-03
Welcome to Ubuntu Forums fire-fly2! :)
> **fire-fly2 said:**
> However after mounting the owner was root.
Probably because you are mounting it by using a script that is run as root? I'm not familiar with the file you are using to mount it, but normal mounting of Vfat filesystem in my Desktop shows a long list of mounting options for the mount point, while you have defined none -
> **fire-fly2 said:**
> PP -fstype=vfat :/dev/sdi1

Please try changing it to (copied the options from my mount command output here) -
```
PP -fstype=vfat,**rw,nosuid,nodev,uid=1000,gid=1000**,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks :/dev/sdi1
```
I'm sure some of the options can be dropped above, but they seem useful for a vfat filesystem, so try it as it is first. Otherwise the options in bold seem to be important to me.

---

