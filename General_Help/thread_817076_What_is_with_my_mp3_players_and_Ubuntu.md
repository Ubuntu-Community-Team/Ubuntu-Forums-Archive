---
title: "What is with my mp3 players and Ubuntu?"
date: 2008-06-03
forum: General Help
---

### Post by jras20 on 2008-06-03
My M230 mp3 player was working fine yesterday morning, then last night I wanted to put a mp3 on to listen while I work out, and now it said its a read only file system?  How do I change that back?  It wont let me in the properties.  I wonder if the updates might of done something to that?  I installed the updates after I used my mp3 player the first time.
If anyone can help me that will be great!
Thanks

---

### Post by jras20 on 2008-06-03
I just dont understand why one minuet it was working great, now it is not.  Both of my Sandisk M230 and M240 now say that the permissions are denied.  Am I just going to half to use XP for these things?  I would like to use Ubuntu on them also if I could!  I'm stuck on this one.

---

### Post by leito666 on 2008-06-03
Its not "protected" right? You know, a kind of button in the side of the MP3.

---

### Post by jras20 on 2008-06-03
Nope, not protected, I cant read or write anything on the mp3 player from data to mp3s.  It just says its a read only drive.

---

### Post by jras20 on 2008-06-03
Let me might add, that Ubuntu will read it as Sandisk m240 drive when I plug it in.  I just cant load anything into it.  Files, mp3s, etc.  It just says permission denied.  This is a read only file system.  I tried formating it in Fat16, 32, everything still nothing please help.
Thanks!

---

### Post by nick_h on 2008-06-03
Did you try both the MTP and MSC modes as suggested in your [previous thread](http://ubuntuforums.org/showthread.php?t=802267)?

---

### Post by jras20 on 2008-06-03
> **nick_h said:**
> Did you try both the MTP and MSC modes as suggested in your [previous thread](http://ubuntuforums.org/showthread.php?t=802267)?

I tried that.  Nothing has changed, it just says permission denied.. on any file, not just mp3.  and I can read the files that are on it.

---

### Post by jras20 on 2008-06-03
On the player it said denied, this is when I try to drag and drop the files, but this is with any files, not just mp3.  There must be something small that I'm not doing.
Here is the screenshot.

---

### Post by nick_h on 2008-06-03
What is the output from:
```
mount
```

Also try:
```
sudo touch "/media/SANSA M240/testfile"
```

---

### Post by SirPerigrin on 2008-06-03
Sounds like a file permissions issue, have you checked the permissions on the files? it may be as simple as 

> sudo chown -R *username* /media/*mountpoint*

---

### Post by jras20 on 2008-06-03
> **SirPerigrin said:**
> Sounds like a file permissions issue, have you checked the permissions on the files? it may be as simple as

Well it does that on every file.  I'll do those codes here in a bit...

---

### Post by jras20 on 2008-06-03
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jras20/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jras20)
/dev/sdb on /media/SANSA M240 type msdos (rw,nosuid,nodev,uhelper=hal)

---

### Post by jras20 on 2008-06-03
> **nick_h said:**
> What is the output from:
```
mount
```

Also try:
```
sudo touch "/media/SANSA M240/testfile"
```

I think those MAY of fixed it!  Lets hope!  Maybe now I can sleep!
:lolflag:  Thanks a bunch lets hope it will keep working!

---

### Post by nick_h on 2008-06-04
I'm glad you got it working but I don't think either of the commands I gave you should actually fix a problem.

The *mount* command was just to give me some information.  The *touch* command would just attempt to create a zero length file on the device.

The output was interesting in that your device mounts as type msdos, mine mounts as vfat. This could give us a starting point if you have further trouble.

I also found an interesting paragraph in the man page for the *mount* command:
> If the msdos file system detects an inconsistency, it reports an error and sets the file system read-only. The file system can be made writeable again by remounting it.

---

### Post by jras20 on 2008-06-04
> **nick_h said:**
> I'm glad you got it working but I don't think either of the commands I gave you should actually fix a problem.

The *mount* command was just to give me some information.  The *touch* command would just attempt to create a zero length file on the device.

The output was interesting in that your device mounts as type msdos, mine mounts as vfat. This could give us a starting point if you have further trouble.

I also found an interesting paragraph in the man page for the *mount* command:

Thats interesting... As long as its working

---

### Post by jras20 on 2008-06-04
I think that command was the one that got it going

sudo touch "/media/SANSA M240/testfile"

---

