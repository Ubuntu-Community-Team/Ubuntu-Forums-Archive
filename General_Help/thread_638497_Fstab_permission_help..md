---
title: "Fstab permission help."
date: 2007-12-12
forum: General Help
---

### Post by Vinno on 2007-12-12
This is what i have so far and its working:

> /etc/fstab
/dev/sda3 /media/MUSIC ntfs-3g defaults,locale=en_US.utf8 0 0


but I need the permission to be
OWNER=root with all permission
GRP=me with all permission
OTHER=no permissions besides read.

Any idea of how to do this?

---

### Post by njparton on 2007-12-12
```

sudo chmod u+rwx /dev/sda3 
sudo chmod g+rwx /dev/sda3
sudo chmod o-rwx /dev/sda3
sudo chmod o+r /dev/sda3

```

change the permissions for the folder you're mounting to using the commands above.

***edit***
I meant /media/MUSIC not /dev/sda3 in each case, ooops

---

### Post by Vinno on 2007-12-12
Doesnt work. All permission stays the same. No error given too.

"sudo chmod o-rwx /media/MUSIC"

---

### Post by kpkeerthi on 2007-12-12
What does 
```

ls -ld /media/MUSIC

```
print?

---

### Post by Vinno on 2007-12-12
drwxrwxrwx 1 root root 4096 2007-12-11 18:44 /media/MUSIC

---

### Post by kpkeerthi on 2007-12-12
1. Unmount the device
```

sudo umount /dev/sda3

```

2. Open /etc/fstab
```

	gksudo gedit /etc/fstab

```

3. Get gid (Group ID) of yours. In terminal, type 
```

	id <your-login-id>

```
It should print something similar to
```

	uid=1000(<your-login-id>) gid=100(users)

```
In this case, the gid is 100.

4. Change 
```

	dev/sda3 /media/MUSIC ntfs-3g defaults,locale=en_US.utf8 0 0  

```
to
```

	dev/sda3 /media/MUSIC ntfs-3g auto,locale=en_US.utf8,uid=0,gid=100,umask=0002  0 0  

```
	Note: Change gid to whatever is applicable for you.
	
5. Mount the partitions with 
```

sudo mount -a

```

6. Check the permission with
```

ls -ld /media/MUSIC

```

---

### Post by Vinno on 2007-12-12
My usergrp id was 1000.
> drwxrwxr-x  1 root vinno  4096 2007-12-12 22:47 MUSIC
WOOO! thanks alot!

Now can the same partition be mounted twice?

say one to /Media/MUSIC for me
then mounting it again for /home/look/download/Music for someone else to so they can access via ftp? (they are jailrooted to their home ~ in vsftpd, so linking doesnt work)


Edit: Seems like "mount --bind /var/ftp/incoming /home/bob/incoming" that i read from [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html) works. Not sure if it will stay on reboot though. Doesnt have any special colour and any indication that i know its a mount/link but its working okay. Cant seem to find any documation/helpfile on mount --blind

Edit2: Damit, doesnt stay after a reboot. Im thinking gotta put it in fstab somehow.

Edi3: For refernce guys, after few google searches and no luck. One person was asking about it too and used "/home/fastbase/tcl /export/apps/fastbase none defaults,bind 0 0" That works, this time mount -a gives me no error :)

---

### Post by kpkeerthi on 2007-12-12
Symbolic link the folder.

```

ln -s /media/MUSIC /home/look/download/Music

```

---

### Post by Vinno on 2007-12-12
> **kpkeerthi said:**
> Symbolic link the folder.

```

ln -s /media/MUSIC /home/look/download/Music

```

Yeah that works but not for ftp users, because they chrooted to their home dir. So cant go out, only option was the mount --bind / fstab thing to get around it.

---

### Post by geirha on 2007-12-12
> **Vinno said:**
> Yeah that works but not for ftp users, because they chrooted to their home dir. So cant go out, only option was the mount --bind / fstab thing to get around it.

Not sure if you can mount ntfs partitions several times, you can with ext3. Anyway, doesn't hurt to try. Just copy/paste the line you added earlier and change the mount-point and gid.

EDIT: Err, I need to get better at actually reading the entire posts before I reply :/

---

### Post by Vinno on 2007-12-12
I dont think its mounting, its more like binding, hence the binding tag used in the fstab. 

So far, the only testing i did was create a simple file in orginal mount directory, then check the folder it binded/linked to, delete the simple test file. Seems like it just works as a -s link.

---

