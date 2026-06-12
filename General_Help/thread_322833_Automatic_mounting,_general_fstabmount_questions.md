---
title: "Automatic mounting, general fstab/mount questions"
date: 2006-12-21
forum: General Help
---

### Post by Gruu on 2006-12-21
I'm sort of new to Linux (but I'm reasonably familiar with the UNIX environment), and I'm running a fresh install of Edgy. I have some CDs that I'd like to read, but whenever I put them in, it mounts them as root (or rather, as user 502), and I can't read them. I could probably just sudo cp the files into my home directory and sudo chmod them so I can read the files, but I'd rather figure out how to make the automatic mount world-readable. Is there any way to do this? I've sort of read through the manpages for fstab/mount, but I already had this line in my fstab:

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

The "user" seems to imply that anyone can mount it, but Ubuntu seems to automatically mount as root. Is there any way to change that setting? Or am I reading the fstab wrong?

Thanks!

---

### Post by kidders on 2006-12-21
Hi there,

You're right about the "user" mount option. It will allow any user to mount the filesystem, but if that user happens to be root, you're right back where you started :-( There is also a "user**_s_**) option, which is slightly different.

You should check your config files & find out who user 502 is. It's likely that your automounter is either running as that user, or deliberately assigning it ownership of mounted filesystems for some reason. The odd thing about this is that most automounters ignore devices listed in /etc/fstab.

If all else fails, and you can't figure out what's going on, you could always manually override the UID & GID applied to stuff on your optical drive with /etc/fstab. Since most CDs and DVDs don't store that information anyway, user & group assignments are pretty arbitrary.

---

### Post by Gruu on 2006-12-21
> **kidders said:**
> Hi there,

You're right about the "user" mount option. It will allow any user to mount the filesystem, but if that user happens to be root, you're right back where you started :-( There is also a "user**_s_**" option, which is slightly different.

You should check your config files & find out who user 502 is. It's likely that your automounter is either running as that user, or deliberately assigning it ownership of mounted filesystems for some reason. The odd thing about this is that most automounters ignore devices listed in /etc/fstab.


Hmm...I'm not too familiar with how UIDs/GIDs work, but when I try

grep 502 /etc/passwd

I get no results (I found "502" as the user and group by right-clicking the files in the CD in the GUI and going to properties->permissions). At this point I'm kind of just going by intuition, but when I do

```

/dev$ ls -l | grep cd
lrwxrwxrwx 1 root root           3 2006-12-21 03:40 cdrom -> hdb
lrwxrwxrwx 1 root root           3 2006-12-21 03:40 cdrw -> hdb
brw-rw---- 1 root **cdrom**     3,  64 2006-12-21 03:40 hdb

```

But I'm in the cdrom group (which I can verify by saying either "groups" or "id")

> 
If all else fails, and you can't figure out what's going on, you could always manually override the UID & GID applied to stuff on your optical drive with /etc/fstab. Since most CDs and DVDs don't store that information anyway, user & group assignments are pretty arbitrary.

How would I do that to get it to work with the automounter? (Or is that possible?)

Thanks for the help! :)

---

### Post by ciscosurfer on 2006-12-21
> **Gruu said:**
> Hmm...I'm not too familiar with how UIDs/GIDs work, but when I try

grep 502 /etc/passwd

I get no results (I found "502" as the user and group by right-clicking the files in the CD in the GUI and going to properties->permissions). At this point I'm kind of just going by intuition, but when I do

```

/dev$ ls -l | grep cd
lrwxrwxrwx 1 root root           3 2006-12-21 03:40 cdrom -> hdb
lrwxrwxrwx 1 root root           3 2006-12-21 03:40 cdrw -> hdb
brw-rw---- 1 root **cdrom**     3,  64 2006-12-21 03:40 hdb

```But I'm in the cdrom group (which I can verify by saying either "groups" or "id")



How would I do that to get it to work with the automounter? (Or is that possible?)

Thanks for the help! :)CDs are always mounted as root:root, however, the CD dev file will also have a block link that placed that device file into the cdrom group as well, of which you are a part.  I've recently mounted a CD to see if my files contained the relationships as yours did...they did not.  Most every file was root:root.  Of course, I'm not having the same issues as you and can read from my CDs just fine.

Have you tried using other CDs to see if this problem is persistent?  Can you play DVD movies (providing you have the appropriate apps to do so)?

I reliaze you want to get this to work at startup.  But for the time being, I would recommend cp'ing over the files you want to read and/or simply using sudo to read them from the disk (use any pager you prefer, or any GUI app that suits your needs).

---

### Post by kidders on 2006-12-21
Hey again,

You might be mixing up two concepts here...

> /dev$ ls -l | grep cd
This will show you whether you have access to the physical devices underlying mounted filesystems, not the filesystems themselves.

My guess is that, for some reason, your automounter daemon is configured to assign UID 502 to mounted devices ... perhaps that ID belongs to a user that no longer exists? I wonder what would happen if you reinstalled it.

My other suggestion involved adding uid & gid options to the /etc/fstab line for your opical drive, in the hope that these would override whatever else is going on. Incidentally, the disc you're trying to read wasn't created on a Mac, by any chance?

---

### Post by Gruu on 2006-12-21
> **kidders said:**
> Hey again,

You might be mixing up two concepts here...


This will show you whether you have access to the physical devices underlying mounted filesystems, not the filesystems themselves.


Ohh, OK. My bad.

> 
My guess is that, for some reason, your automounter daemon is configured to assign UID 502 to mounted devices ... perhaps that ID belongs to a user that no longer exists? I wonder what would happen if you reinstalled it.

My other suggestion involved adding uid & gid options to the /etc/fstab line for your opical drive, in the hope that these would override whatever else is going on. Incidentally, the disc you're trying to read wasn't created on a Mac, by any chance?

...yes, it was. I just tried other CDs, and they work, apparently....is there a known issue with CDs created by macs not working properly?

Thanks for all the help! I guess I'll just copy the mac-created one to my HD for now.

---

### Post by kidders on 2006-12-21
> is there a known issue with CDs created by macs not working properly?No... it was just a guess. MacOS is more easily capable of storing ownership & permissions on CDs than Windoze is, and on a Mac, 502 is usually the UID assigned to the second account added to a machine (just as 1001 would be on Ubuntu).

Whoever created the CD you were experimenting with decided to burn it with a permissions/ownership-capable filesystem (maybe HFS). God knows why, but needless to say, they won't map sensibly to actual accounts anywhere except on his own machine.

Strange problem, but at least we found the cause :-)

**Edit:** For this specific disc, you could try mounting it manually with:```
sudo mount -o uid=1000,ro /dev/hdb /mnt/wherever
```This *should* force ownership by user 1000 (presumably you?) on it. All other CDs (including ones made on a Mac) should work normally with your existing system settings.

---

