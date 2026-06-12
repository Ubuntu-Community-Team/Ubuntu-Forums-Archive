---
title: "Can no longer write to iPod"
date: 2005-05-26
forum: General Help
---

### Post by angkor on 2005-05-26
I have a strange problem. My 4g iPod (connected with USB) used to work perfectly with Ubuntu 5.04. I haven't used it in a couple of days and today I am no longer able to write the iTunesDB. This is making it impossible to sync with gtkpod.

I used to ```
sudo mount /mnt/ipod
``` 
and ```
sudo gtkpod
``` and it worked flawlessly until today.

Here is my (unchanged) fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda8       /download       ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6       /usr            ext3    defaults        0       2
/dev/hda7       /var            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0         /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2	/mnt/ipod	vfat	defaults,user,noauto	0	0

``` 

I did'nt make any major changes to the system except for the usual updates which included a new linux-image a couple of days ago.


Anyone have any clue?

Grtz,

Angkor

---

### Post by angkor on 2005-05-26
Hmm it seems mounting is not the problem. This is my dmesg output *after* I read the iTunesDB with gtkpod:

```
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218697)
    File system has been set read-only
FAT: Filesystem panic (dev sda2)
    fat_bmap_cluster: request beyond EOF (i_pos 1218697)
```

After mounting it dmesg doesn't give me any errors.

Seems like there's something wrong with the iPod itself....Well it still plays my songs sweetly so maybe I'll try to reformat it when I come across a Windoze machine :(

---

### Post by astoltz on 2005-05-26
I had this problem a while back and unfortunately I can't remember exacty what fixed it.  It had something to do with installing the HFS+ tools and then using those to mount / unmount the iPod - something like "sudo hfmount /mnt/ipod".  Sorry I'm short on details but I'm not at my Ubuntu machine right now.  HFS+ is apt-get able - but you probably have to enable the universe repository. 

Also, using ```
sudo eject /mnt/ipod
``` makes the "do not disconnect" message on the ipod go away and I've not had the problem re-occur.

---

### Post by astoltz on 2005-05-26
[QUOTE=astoltz]I had this problem a while back and unfortunately I can't remember exacty what fixed it.  It had something to do with installing the HFS+ tools and then using those to mount / unmount the iPod - something like "sudo hfmount /mnt/ipod".  Sorry I'm short on details but I'm not at my Ubuntu machine right now.  HFS+ is apt-get able - but you probably have to enable the universe repository. 

Also, using ```
sudo eject /mnt/ipod
``` makes the "do not disconnect" message on the ipod go away and I've not had the problem re-occur.[/QUOTE]
 Whooops, I just read you second post and since your Ipod is formatted as a FAT filesystem,  HFS trick I was referring to will obviously not work.

---

### Post by angkor on 2005-05-26
[QUOTE=astoltz]Whooops, I just read you second post and since your Ipod is formatted as a FAT filesystem,  HFS trick I was referring to will obviously not work.[/QUOTE]

 :smile: Never mind

I didn't really mind pulling the ipod free after unmounting it with the 'do not disconnect' sign still on, it has never given me any trouble. Just wonder what fscked up my ipod's filesystem.

I wish there were a ext2 Ipod. :)

---

### Post by astoltz on 2005-05-26
I wonder if disconnecting before the iPod is ready to be removed isn't causing some kind of file system screw-up.  The "eject" command is available as part of the standard Ubuntu install and I always use that instead of umount - no problems since.

---

### Post by angkor on 2005-05-27
[QUOTE=astoltz]I wonder if disconnecting before the iPod is ready to be removed isn't causing some kind of file system screw-up.  The "eject" command is available as part of the standard Ubuntu install and I always use that instead of umount - no problems since.[/QUOTE]

Don't think so. It actually is ready to be removed after you unmount is. The disc stops spinning. The icon blinking is just some thingie apple provided in combination with iTunes I think. I used to do this all the time on Debian and later Ubuntu as well.

---

### Post by angkor on 2005-06-03
Solved the problem using: sudo dosfsck dev/sda2 found in the Tips & Tricks forum.

It automatically repaired the filesystem

---

### Post by larry_steiner on 2005-09-21
Trying to do a sync but I can't seem to get the IPOD out of read only.  I did this as root too.  Any ideas?  Thanks for the help.

rwx------   7 larry larry 4096 1969-12-31 19:00 IPOD
drwxr-xr-x   2 root  root  4096 2005-09-21 18:20 usbdisk
larry@ubuntu:/media$ chmod 777 IPOD
chmod: changing permissions of `IPOD': Read-only file system
larry@ubuntu:/media$ ls -la
total 24
drwxr-xr-x   6 root  root  4096 2005-09-21 19:35 .
drwxr-xr-x  22 root  root  4096 2005-09-13 04:26 ..
lrwxrwxrwx   1 root  root     6 2005-09-13 04:18 cdrom -> cdrom0
drwxr-xr-x   2 root  root  4096 2005-09-13 04:18 cdrom0
drwxr-xr-x   2 root  root  4096 2005-09-13 04:18 cdrom1
drwx------   7 larry larry 4096 1969-12-31 19:00 IPOD

---

### Post by larry_steiner on 2005-09-22
Did a chown as root, the command ran but did not change the owner.  Did a chgrp no luck.  Tried recursive chmod, no luck.  Finally,  got things working here what I did:

I copied all the data from the IPOD to my main file system.  

Did a chmod -R 777 * on the Ipod files (local file system).

Put the IPOD on a Windoz machine and did a full disk FAT32 format.  

Mounted the IPOD and copied all the data back (with the new permissions).

---

