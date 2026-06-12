---
title: "Can't mount as user, or write to drives"
date: 2007-07-25
forum: General Help
---

### Post by iPat on 2007-07-25
I've seen plenty of threads on editing fstab, and I thought I edited it properly but apparently not. I've been able to get my drives to auto-mount but they always end up mounting with no write permissions (as root I suppose), effectively making them useless to me. Also, if I want to mount them from the terminal, I have to do it using sudo as the root, otherwise it says "only root can do that". Here's what my fstab looks like:

```

# Entry for /dev/hda1 (PRIMARY HD) :
UUID=a13a6f91-0d39-412e-b20e-604e01e634f7 / ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/hda5 (SD CARD) :
UUID=52aba89e-6e15-426e-9c59-e772fca2c14c none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

#Entry for /dev/hdb1 (MEDIA HD) :
/dev/hdb1 /media/media vfat rw,auto,user,sync,exec 0 0

#Entry for /dev/sdb1 (EXTERNAL HD) :
/dev/sdb1 /media/encrypted ext3 rw,auto,user,sync,exec 0 0

```

I thought by doing the "rw,auto,user" it would give any user permission to write to the drive, however it's still not doing it.

So then I tried using Chmod -r and Chown -r by running the following commands:

```

sudo chown -R pat:pat /media/media
sudo chmod -R 777 /media/media

```

but Chown just returns operation not permitted for every file. 

Some help would be greatly appreciated. These drives are useless to me without being able to write to them.

---

### Post by iPat on 2007-07-26
Still haven't been able to figure this out. I've read tons of threads related to it, but can't find the problem. Anyone have any suggestions?

---

### Post by AceofSpades19 on 2007-07-26
did you try doing that stuff as root by using sudo?

---

### Post by vanadium on 2007-07-26
```

man mount

```
will tell you about the various options. user means that a user can mount/unmount the device. For the permanent drives that you mount automatically, there is no need that the user can mount/unmount, thus the user option is not needed. For the removable devices, you should not need an entry in fstab. Ubuntu will automatically mount removable devices with read/write permissions for the user.

The actual permissions of the root of the mounted device is governed by the permissions of the mount point. If you want to own a root directory as a user, then you should chown the mount point (e.g. /media/media). Alternatively, if you want everyone to be able to read/write/execute on the drive, then you should set the other permissions as such.

Thus, for your /media/media, try

```

sudo chown <yourusername>:<yourgroupname> /media/media
[code]

or alternatively (moint point remains owned by root, but anyone can read/write/execute)

[code]
sudo chmod 777 /media/media

```

I would not include anything that can be removed, such as you external hd and even more typically your SD card in fstab, but have Ubuntu handle this automatically.

---

### Post by bitonw on 2007-09-15
sure but this is still not working for me... why is ubuntu so difficult with mount... i even made the local users a member of the group users...

get tired of this

---

### Post by tom_mc on 2007-10-13
This is the same problem I have been having.. it is a pain in the A$$. I can't believe this is not doable. WTF:confused::mad:

---

### Post by bodhi.zazen on 2007-10-13
> **tom_mc said:**
> This is the same problem I have been having.. it is a pain in the A$$. I can't believe this is not doable. WTF:confused::mad:

Well this is an old thread ....

The problem is that windows partitions do not support linux ownership or permissions.

They are, however, set at the time of mount .

Using the OP example : 

> **iPat said:**
> 

I thought by doing the "rw,auto,user" it would give any user permission to write to the drive, however it's still not doing it.

So then I tried using Chmod -r and Chown -r by running the following commands:

```

sudo chown -R pat:pat /media/media
sudo chmod -R 777 /media/media

```

but Chown just returns operation not permitted for every file. 

Some help would be greatly appreciated. These drives are useless to me without being able to write to them.

You need to mount like this :

```
sudo mount -t vfat /dev/hdb1 /media/media -o uid=1000,gid=100,umask=007
```

Or put this in fstab :
> /dev/hdb1 /media/media vfat auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0

Then mount with :```
mount /media/media
```Or "mount /dev/hdb1"

As vanadium said, this is in [man mount](http://linux.die.net/man/8/mount), ***but you need to look at the section for vfat*** :twisted:

See if this link helps : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by tom_mc on 2007-10-13
Great,Thank You so much! :-)

---

