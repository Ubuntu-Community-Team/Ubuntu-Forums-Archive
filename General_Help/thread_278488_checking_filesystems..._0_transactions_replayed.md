---
title: "checking filesystems... 0 transactions replayed"
date: 2006-10-16
forum: General Help
---

### Post by hecato on 2006-10-16
Hi there, when I start my PC, in some place of entering to logon screen (ini init), I get something like:

> 
Checking internal tree finished
                                                                            [ok]
 * Starting RAID devices...                                                                             [ok]
 * Setting up LVM Volume groups                                                                            [ok]
 * Starting Enterprise Volume management System...                                                                             [ok]
 * Checking all filesystems...
 Reiser superblock in block 16 on 0x306 of format 3.6 with standar journal
 Blocks (total/free): 767088/210412 by 4096 bytes
Filesystem is clean
Replaying journal...
Reiserfs journal '/dev/hda6' in blocks [18..8211]: 0 transactions replayed
(or type control-D to continue):ehell and continue system startup0.laye[ok]



Like you see the last line is overlapped with 2 different messages, also it ask me for root password or control-D for continue.


I hit control-D, because I really dont know what to do in for maintain it :P...



It work ok, but I have restarted, and the error stills show at startup, what to do¿?¿?¿?


That partition is where I have my "/home" mount point (hda6)

```

~$ mount
/dev/hda7 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-amd64-k8/volatile type tmpfs (rw)
/dev/hda6 on /home type reiserfs (rw)
/dev/hda3 on /mnt/hda3 type reiserfs (rw,nosuid,nodev)
/dev/hda8 on /programador type reiserfs (rw,nosuid,nodev)
/dev/hda9 on /repos type reiserfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

