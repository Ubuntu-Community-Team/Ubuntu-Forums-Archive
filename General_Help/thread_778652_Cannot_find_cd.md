---
title: "Cannot find cd"
date: 2008-05-02
forum: General Help
---

### Post by crow_se on 2008-05-02
I am trying to install Call of Duty on Ubuntu 7.04 using Wine.
The first cd installs ok, and I am then asked for the second cd. I eject the first using wine eject and put cd 2 into the pc. The cd is mounted but the system cannot seem to find it, I keep getting the 'Insert cd 2' dialog over and over again. The cd is mounted and I can access it and the files on it from a terminal or from Nautilus.
I dont know if this is a Ubuntu problem or a Wine problem so I am posting in both forums.

---

### Post by crow_se on 2008-05-02
I am trying to install Call of Duty on Ubuntu 7.04 using Wine.
The first cd installs ok, and I am then asked for the second cd. I eject the first using wine eject and put cd 2 into the pc. The cd is mounted but the system cannot seem to find it, I keep getting the 'Insert cd 2' dialog over and over again. The cd is mounted and I can access it and the files on it from a terminal or from Nautilus.
I dont know if this is a Ubuntu problem or a Wine problem so I am posting in both forums.

---

### Post by soxs on 2008-05-02
Type ```
mount
``` into terminal.
If CD2 is NOT mounted at the same folder as CD1, the installer will not detect it.
Plx add your /etc/fstab here, there migth lie your problem (had some mess up with etcfstab and my IDE cdrom drive)
Note: In general I suggest you to copy the files from your cds into one folder to your hd and launch the installer from there.

---

### Post by crow_se on 2008-05-02
Thanks for the reply.

mount gives the following :
/media/host/wubi/disks/system.virtual.disk on / type ext3 (rw,sync)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/media/host/wubi/disks/home.virtual.disk on /home type ext3 (rw,sync,loop=/dev/loop1)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/CoD2 type iso9660 (ro,nosuid,nodev,uid=1000,utf8)

and fstab:
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop
,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,s
ync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw    
            0   0

cd1 is labelled COD1 and cd2 is labelled COD2, both are mounted as /media/cd label -
is this what you meant by 'If CD2 is NOT mounted at the same folder as CD1, the installer will not detect it.'

I am not sure about copying all files to a folder because of multiple files and folders with the same name.

This is the first time I have tried anything like this as a new user, so please excuse my being a bit thick.

---

### Post by soxs on 2008-05-02
> **crow_se said:**
> Thanks for the reply.

mount gives the following :
/media/host/wubi/disks/system.virtual.disk on / type ext3 (rw,sync)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/media/host/wubi/disks/home.virtual.disk on /home type ext3 (rw,sync,loop=/dev/loop1)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/CoD2 type iso9660 (ro,nosuid,nodev,uid=1000,utf8)

You got the problem I had..
> **crow_se said:**
> 
and fstab:
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop
,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,s
ync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw    
            0   0

I can not believe that this is your whole fstab!
> **crow_se said:**
> 
cd1 is labelled COD1 and cd2 is labelled COD2, both are mounted as /media/cd label -
is this what you meant by 'If CD2 is NOT mounted at the same folder as CD1, the installer will not detect it.'

I am not sure about copying all files to a folder because of multiple files and folders with the same name.

This is the first time I have tried anything like this as a new user, so please excuse my being a bit thick.

I suggest you to add this line to your /etc/fstab, which will make cds/dvds always mount at cdrom0 (or cdrom# if you have more than one cddrive, # being the number of your cd drive) (mnake sure that an empty folder named cdrom0 (or cdrom# if you have more than one cddrive) exists):

```
/dev/hdc       /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0       0
```

And for the multiply dublicates, simply copy everythin into one folder, if something gets overriden, do not care about. You will see finally if the installer runs through. It's always like cubing if it works with wine or not.

For future posts and an increase of readability, plx use [CODE]-tags

---

### Post by cogadh on 2008-05-02
Its a known bug in Wine with the CoD installer. You cannot install CoD normally in Wine, you'll need to use either the old Loki install script (if you can still find it) or something like PlayOnLinux.

---

