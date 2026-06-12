---
title: "FAT32 Problem"
date: 2004-10-29
forum: General Help
---

### Post by TravisNewman on 2004-10-29
OK I know that there have been plenty of problems with accessing NTFS partitions in Linux, but I'm having trouble with my FAT32 drive that I use for transferring files back and forth between the two OS's. I can mount it fine, and I can access it, but I can't write to it. I know that I've been doing that since RedHat 5, so I know it's possible. What should the line in /etc/fstab look like. I THOUGHT all I had to do in the past was make it a vfat and set the rw and user options.

Another problem that I have is that if I have it set to automount, even with rw and user, when I first try to access it, it gives me the familiar problem of everything, even directories, showing up as executable files. I have to unmount then with sudo, then mount it without the sudo, and I can get to everything fine. I've added dmask=0222 and fmask=0333 and those seem to have fixed THAT problem. But I still can't write to the drive.

---

### Post by HungSquirrel on 2004-10-29
My line looks like this.

```
/dev/hda2	/fat		vfat	rw,user,users,uid=1000	0 0
```

---

### Post by TravisNewman on 2004-10-29
Nope, that didn't work either. I still can't write to it at all.

---

### Post by HungSquirrel on 2004-10-29
Sounds like you're screwed.  8)

---

### Post by TravisNewman on 2004-10-29
[QUOTE=HungSquirrel]Sounds like you're screwed.  8)[/QUOTE]
 Well I certainly hope not. I know there has to be a way to do it.

---

### Post by Joeb on 2004-10-29
Try this in the /etc/fstab:

/dev/hda1     /mnt/windows     auto     rw,user,auto,umask=000  0   0

Of course, you will need to substitute the proper partition for hda1 and the mount point for /mnt/windows.


The problem that you are having is because it is being automounted before you log in and therefore you don't have access to it, because you're not the owner.  I think the above line will fix it for you.

Joeb

---

### Post by FLeiXiuS on 2004-10-29
[QUOTE=Joeb]Try this in the /etc/fstab:

/dev/hda1     /mnt/windows     auto     rw,user,auto,umask=000  0   0

Of course, you will need to substitute the proper partition for hda1 and the mount point for /mnt/windows.


The problem that you are having is because it is being automounted before you log in and therefore you don't have access to it, because you're not the owner.  I think the above line will fix it for you.

Joeb[/QUOTE]


/dev/hda1     /mnt/windows     vfat     rw,uid=1000,gid=1000,umask=0000  0   0

This is what I would reccomend

---

### Post by TravisNewman on 2004-10-29
[QUOTE=FLeiXiuS]/dev/hda1     /mnt/windows     vfat     rw,uid=1000,gid=1000,umask=0000  0   0

This is what I would reccomend[/QUOTE]
 Flexius, tried yours first, and it works mostly, but a few of the folders and files are still locked. I don't know why, but I can still write to the drive which is what I needed. It seems that the folders with a desktop.ini inside are the ones that are locked.

---

### Post by Joeb on 2004-10-29
[QUOTE=FLeiXiuS]/dev/hda1     /mnt/windows     vfat     rw,uid=1000,gid=1000,umask=0000  0   0

This is what I would reccomend[/QUOTE]


Wouldn't the uid/gid parts cause problems for other users on the system who may need to mount/umount the partition?

---

### Post by FLeiXiuS on 2004-10-29
[QUOTE=Joeb]Wouldn't the uid/gid parts cause problems for other users on the system who may need to mount/umount the partition?[/QUOTE]


Only the GID, where as if he wants this to be accessable by all others, then he should set that users GID to 1000.

---

### Post by TravisNewman on 2004-10-30
[QUOTE=FLeiXiuS]Only the GID, where as if he wants this to be accessable by all others, then he should set that users GID to 1000.[/QUOTE]
 There are no other users on this system, and even if there were I wouldn't want them to have access to that drive anyway, so it works. I actually took out the gid because it didn't seem to matter.

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=panickedthumb]There are no other users on this system, and even if there were I wouldn't want them to have access to that drive anyway, so it works. I actually took out the gid because it didn't seem to matter.[/QUOTE]

UID/GID
These 2 parameters set the ownership of the mounted filesystem.

---

### Post by TravisNewman on 2004-10-31
[QUOTE=FLeiXiuS]UID/GID
These 2 parameters set the ownership of the mounted filesystem.[/QUOTE]
 Yeah I know, but I was experimenting and taking out GID didn't make it stop working.

---

