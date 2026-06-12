---
title: "Automount External Drive to Specific Mount Point"
date: 2008-03-14
forum: General Help
---

### Post by odie5533 on 2008-03-14
I am trying to get my external hard drive to automatically mount to /media/WD ES 500GB when I plug it in. I have set permissions on the folder, and I can mount it there manually using:
```
sudo mount /dev/sdc2 /media/WD\ ES\ 500GB
```
but it won't automatically mount there. Instead, it mounts itself to /media/WD\ ES\ 500GB_, and I need to umount and mount it to the right place manually. I was wondering how I can set it to automatically mount to the same place, the one with permissions set. I tried using fstab:
```
UUID=59855B7629079358	/media/WD\040ES\040500GB	ntfs-3g	auto,user 0 0
```
But that doesn't work and I'm not even sure fstab is the right file to edit to make this work.

Any help is greatly appreciated.

---

### Post by danwood76 on 2008-03-14
Fstab is the correct place but linux doesnt really like spaces in paths etc.
try it without spaces and with an underscore instead and you might have more luck.

---

### Post by odie5533 on 2008-03-14
No better. It says unprivileged user can not mount ntfs block device using the external FUSE.

---

### Post by danwood76 on 2008-03-14
can you post
```

cat /etc/fstab

```

you need to use sudo to mount stuff thats not allowed in the fstab (with user permissions)

---

### Post by odie5533 on 2008-03-14
I was looking for a way to have it mount by itself so I wouldn't have to sudo mount every time I plug the thing in =/

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cea90fcc-2538-454e-b4b7-46e4db8342bf /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=b2a9b824-56e6-4080-8c08-db37c2d5ccc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# WD ES 500GB
UUID=59855B7629079358	/media/WD500GB	ntfs-3g	auto,user 0 0
```

---

### Post by odie5533 on 2008-03-14
I am still trying to solve this. Every time I plug the hard drive in that error comes up. I can get it to atuomount but it still refuses to automount to the directory I've already made.

---

### Post by danwood76 on 2008-03-15
do a
```

sudo gedit /etc/fstab

```
and modify the line in the fstab to be:
```

UUID=59855B7629079358	/media/WD500GB   ntfs-3g   defaults   0 2

```
I think you are loading the wrong privaliges and settings when it auto mounts (the above works on my internal NTFS drives)

also you need to create the directory /media/WD500GB and chown it to yourself

---

### Post by odie5533 on 2008-03-15
```
sudo mount -a
``` will do the trick, but it won't automatically do that when I plug in the drive. I tried changing the line to what you posted but it still has the same problem when I plug the drive in, no permissions.

---

### Post by danwood76 on 2008-03-15
To mount as a user you need to add the user option and not defaults.
So the line should look like this:
```

UUID=59855B7629079358	/media/WD500GB   ntfs-3g   rw,auto,user,sync  0 2

```

If 'mount -a' then works as normal user you should be good to go.

---

### Post by odie5533 on 2008-03-15
Still same problem. I did
```
sudo chown odie:odie /bin/mount
```
and I can now do mount -a on my normal user. But it gives me the following error:
```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

---

### Post by danwood76 on 2008-03-16
Following the link from that output I did a quick test on my system and it seems running these 2 comnmands might solve your problem (at least it worked on mine with ntfs-3g)

```

sudo chown root $(which ntfs-3g)
sudo chmod 4755 $(which ntfs-3g)

```

After doing this I could then mount my ntfs drives as a normal user, I would also change the ownership of mount back to root for security reasons. (I didnt have to change ownership to get it working just the 2 commands above)
```

sudo chown root:root /bin/mount

```

---

### Post by odie5533 on 2008-03-16
Nope, still with the same error coming up that says it is unprivileged.

---

### Post by danwood76 on 2008-03-16
Strange it worked on my internal drives.
I will have a play with my external drive tomorrow.

---

### Post by odie5533 on 2008-03-17
If anyone else has any ideas on this I'd really appreciate it as I'm still stuck mounting this thing by hand each time I plug it in =/

---

### Post by dmonkey on 2008-05-01
Hi,

The reason why you get the underscore after the name is probably because the directory already exists. Try removing the directory (Linux should create it automatically when the drive is inserted).

---

### Post by wzzrd on 2008-05-06
> **odie5533 said:**
> Nope, still with the same error coming up that says it is unprivileged.

It's actually another error message. When you chmod the file to be setuid root, the error messages becomes something that tells you setuid is bad and that it won't work with setuid :)

Anyway, I consider ntfs-3g broken this way, and there seem to be some bugreports about it too...

See: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081)

---

### Post by shinobitux on 2008-05-12
I've had the exact same problem and I've been looking for solutions on my own. Some Ubuntu systems I have automatically mount external devices while others require me to do the "sudo mount /dev/sdx1 /media/mountpoint" thing.

For a given run I've had success with editing the /etc/fstab but on restart it doesn't succeed.

I haven't tried this on my own yet but it might have something to do with the udev automount rules.

Try this thread I found: [http://ubuntuforums.org/showthread.php?t=168221&highlight=automount+devices](http://ubuntuforums.org/showthread.php?t=168221&highlight=automount+devices)

---

### Post by gavinjb on 2008-05-24
Hi,

I had a similar problem for my external ext3 drive and I had to do the following while the drive was not mounted

sudo chown myuser:myuser /media/mydrive
sudo chmod +rw /media/mydrive

not sure if this helps, my setup was a bit different though as I had a udev rule rather than using a UID

---

