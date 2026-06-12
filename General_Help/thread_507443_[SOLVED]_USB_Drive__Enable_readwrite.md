---
title: "[SOLVED] USB Drive : Enable read/write"
date: 2007-07-23
forum: General Help
---

### Post by shankariyer on 2007-07-23
Hello,

I read the forum and followed few other pointers, but no luck.

I'm trying to mount my USB drive in read/write mode. Initially /etc/fstab didn't have any entry to auto-mount and neither was my USB drive connected all the time.

Now, I'd like to read/write.

Whenever I mount it manually ( using gnome partition editor ) it mounts only in read-only mode.

The last try was using ntfs-fuse with the following entry in /etc/fstab but this also doesn't work - it doesn't even auto-mount, but when I mount manually, again it mounts only in read-only. Please advice. THanks.

/dev/sda5 /media/usb_drive ntfs-fuse fmask=0111,dmask=0,locale=en_US.utf8 0 0

---

### Post by aquavitae on 2007-07-23
You shouldn't need an fstab entry for a usb drive - it should be automatically mounted by udev.  Did it mount at all before you entered it into fstab?

According to your fstab entry, the usb drive is ntfs - is this correct?  Is it a hard drive or a flash drive - flash is not usually ntfs. Have you tried the ntfs-3d drive: [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

Assuming all the above is correct, try adding the following to the list of options in the fstab entry (i.e. next to fmask, dmask, etc): ```
users,rw,auto
```

---

### Post by bodhi.zazen on 2007-07-23
If you want to do it with a gui, take a look at nfts-config. It is a front end for ntfs-3g

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by shankariyer on 2007-07-23
This is an 3.5" external hard-drive ( 120gb capacity )

Initially I didn't have any fstab entry and it did mount but in read-only mode.
If there is a way to make that auto-mount read/write, that's all I want. In fact,
this is consistent as how it has mounted other windoze drives (5 of them) also.

Thanks.

---

### Post by bodhi.zazen on 2007-07-23
Could you give a few more details ?

Have you installed ntfs-3g or ntfs-config ?

Also I believe you should remove your entry in fstab if you want to automount, but I am not positive with ntfs-3g

Your options in fstab would be something like :

users,noauto,uid=1000,gid=100,umask=000

"noauto" = do not mount at boot (not no auto mount when plugged in).

---

### Post by shankariyer on 2007-07-24
Bodhi,

Sorry about that...

ntfs-3g and ntfs-progs are installed as I see in the Synaptic Package Manager.
ntfs-config was not, but now I installed it.

Please give me the full /etc/fstab entry as I'm not sure of whether I should give 'ntfs' or 'ntfs-fuse' or 'vfat' for the file-system

This is what I've now, after I modified based on the above suggestion.
#USB Drive
/dev/sda5 /media/usb_drive ntfs users,noauto,uid=1000,gid=100,umask=000

Thanks !

---

### Post by shankariyer on 2007-07-25
Update...
I have this now
> /dev/sda5 /media/usb_drive ntfs rw,users,noauto,uid=1000,gid=1000 0 0 #,umask=555
and 'rw' doesn't seem to work. It mounts with read and execute if I remove rw and add umask=000. Played with those umask numbers, but it doesn't work.

Please advice.

---

### Post by shankariyer on 2007-07-25
umask of 066 is not creating the directory with the desired 700 permission - 
not sure what the issue is ????

---

### Post by bodhi.zazen on 2007-07-25
> **shankariyer said:**
> umask of 066 is not creating the directory with the desired 700 permission - 
not sure what the issue is ????


LOL

umask 077 = Permissions 700

Prmission = 7 - <umask value>

So umask 066 = permissions of 711

Try :

uid=1000, gid=1000,umask=077

---

### Post by vanadium on 2007-07-25
You should not be tinckering with the config files to get your usb drives mounted. Just install ntfs-config along, load it and check the box "Enable write support for external drives". This will configure the system to use the ntfs-3g driver for ntfs partitions. My advise is:

* first remove the fstab entry you put there
* type "sudo mount-a" to apply the updated fstab file
* Run ntfs-config, check the appropriate box

My experience is that Nautilus can act a bit weird in the root directory of the drive. It behaved as if the drive was still read only. However, I could without a problem drag a directory onto the drive. Once in a subdirectory, Nautilus behaves normally.

For your information: for permanently mounting using ntfs-3g you would need to specify ntfs-3g and not ntfs as the file system in your fstab.

---

### Post by Atomic Dog on 2007-07-25
> **vanadium said:**
> You should not be tinckering with the config files to get your usb drives mounted. Just install ntfs-config along, load it and check the box "Enable write support for external drives". This will configure the system to use the ntfs-3g driver for ntfs partitions. My advise is:

* first remove the fstab entry you put there
* type "sudo mount-a" to apply the updated fstab file
* Run ntfs-config, check the appropriate box

My experience is that Nautilus can act a bit weird in the root directory of the drive. It behaved as if the drive was still read only. However, I could without a problem drag a directory onto the drive. Once in a subdirectory, Nautilus behaves normally.

For your information: for permanently mounting using ntfs-3g you would need to specify ntfs-3g and not ntfs as the file system in your fstab.

This worked for me.  Just installed ntfs-3g, ntfs-config, ran ntfs-config and ticked the read/write for external drives, rebooted and the drive was mounted with read/write enabled.  This makes my like a lot easier as I really needed external storage.  Thanks!

---

### Post by shankariyer on 2007-07-26
Vanadium,

Great pointer ! Thanks...

Few issues... enabled write support for external drives & removed /etc/fstab & mount -a also...

When I powered the drive, it complained of ntfs $LOGFILE being corrupt and that to run ntfsfix, I did and ntfsfix completed successfully.

It wouldn't still mount automatically, but it suggests now
> mount -t ntfs-3g /dev/sda5 /media/USB Drive -o force

This does work, but I'm doing it manually at the shell prompt and I'm able to umount only at the shell prompt.

Latest message
> 
~$ sudo mount -t ntfs-3g /dev/sda5 /media/usb_drive
Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sda5 /media/usb_drive -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sda5 /media/usb_drive ntfs-3g defaults,force 0 0



---

