---
title: "Swap not working"
date: 2007-01-14
forum: General Help
---

### Post by icefaerie on 2007-01-14
Hello!

I'm having a problem with my swap partition.  For whatever reason, it's not activating.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 / reiserfs defaults 0 1
# /dev/hda3 -- converted during upgrade to edgy
/dev/hda3 /boot ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
/dev/hda2 /mnt/share vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
/dev/hda1 /mnt/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 swap swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

But it's not mounted:
```
liz@sirius:~$ mount
/dev/hda6 on / type reiserfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda3 on /boot type ext3 (rw)
/dev/hda2 on /mnt/share type vfat (rw,utf8,umask=007,gid=46)
/dev/hda1 on /mnt/windows type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

I have tried swapon but it's not working:
```
liz@sirius:~$ sudo swapon /dev/hda5
swapon: /dev/hda5: Invalid argument
```

I didn't realize my swap wasn't on until I checked top because my computer was being horrendously slow.

---

### Post by taurus on 2007-01-14
```
/dev/hda5  **none**   swap   sw   0   0
```

---

### Post by vigleik on 2007-01-14
Maybe the swap partition has been damaged somehow, and is no longer being recognized as a swap partition (happened to me before, don't know why). The fix is to reformat the swap partition. For example (though there's probably an even easier way), you can boot from the live CD, run gparted (or qtparted, or whatever) and delete and recreate the swap partition.

EDIT: taurus' way using mkswap seems much easier than what I suggested.

---

### Post by taurus on 2007-01-14
> **vigleik said:**
> Maybe the swap partition has been damaged somehow, and is no longer being recognized as a swap partition (happened to me before, don't know why). The fix is to reformat the swap partition. For example (though there's probably an even easier way), you can boot from the live CD, run gparted (or qtparted, or whatever) and delete and recreate the swap partition.

Applications -> Accessories -> Terminal
```
sudo mkswap /dev/hda5
sudo swapon /dev/hda5
```

---

### Post by icefaerie on 2007-01-14
> **taurus said:**
> ```
sudo mkswap /dev/hda5
sudo swapon /dev/hda5
```

Thanks, that did the trick!

---

### Post by theboatashore on 2007-01-20
Thanks.  I've been having this problem for a while and this has solved it.

---

### Post by Timothy S on 2007-01-22
having this problem too, I've done everything in this thread:

fstab:
/dev/hda2 none swap sw 0 0

$ sudo mkswap /dev/hda2 
Setting up swapspace version 1, size = 1305014 kB
no label, UUID=af9e9e73-53bf-43f6-a1b3-5f1b6d642017
$ sudo swapon /dev/hda2 
swapon: /dev/hda2: Device or resource busy


Why does it say busy?

---

