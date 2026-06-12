---
title: "&quot;dd&quot; Command Issues while Following Tutorial on VMWare"
date: 2007-02-14
forum: General Help
---

### Post by SendDerek on 2007-02-14
Hello all!

I am following [this tutorial]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") and I cannot get any further than this step:

> 
Type "quit" in parted and make copy of MBR. Copy-paste this command into console:
"dd if=/dev/hda of=windowsxp.mbr bs=512 count=63"


I get this error message:
> 
dd: opening `/dev/hda': No medium found


Is there something that I am doing wrong?  I have followed all of the steps with no problems thus far.  I can see that there is in fact a "file" called hda in the dev directory.  I don't understand why there is no media being found.

I have XP Pro installed just fine now on one of my partitions.  Here is the output of gnu parted if this can help:
```

Number  Start      End         Size        Type      File system  Flags
 1      63s        20482874s   20482812s   primary   ntfs         boot 
 2      20482875s  195366464s  174883590s  extended               lba  
 5      20482938s  23567354s   3084417s    logical   linux-swap        
 6      23567418s  54283634s   30716217s   logical   ext3              
 7      54283698s  195366464s  141082767s  logical   ext3              

```

Help? 

Thanks in advance!

-Derek

BTW: I'm running Edgy...

---

### Post by bettlebrox on 2007-02-14
Usually the first IDE drive on a system is hda. Your drive could be hdb or hdc or hdd ... or sda or sdb if your using a SATA drive. What's the output of the mount command? (Open a terminal and type mount).

---

### Post by SendDerek on 2007-02-14
Thank you for your reply!

Here is the output for the 'mount' command:

```

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw)
/dev/disk/by-uuid/4894444594443828 on /media/windows type fuse (rw,nosuid,nodev,noatime,allow_other)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

Also, this is on a laptop if that makes any difference.

---

### Post by SendDerek on 2007-02-14
Sweet... I think I got it.

I tried it with "sda" instead of "hda" and it seemed to have worked.

Thank you much for your help!  I'm onto the next step in the tutorial then!

---

### Post by bettlebrox on 2007-02-15
Yup, sda looks like the first hard drive on your system, probably a SATA or PATA drive. Glad that worked! :)

---

