---
title: "fstab"
date: 2007-02-27
forum: General Help
---

### Post by qoheleth on 2007-02-27
I screwed up my fstab so that I can't boot in linux anymore so I've mounted it on a live boot and now I'm staring blankly at my fstab can anyone tell me what's up.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=206a6b45-5183-4e21-af73-e17dcaea8abd / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
UUID=4AE820A8E820946B /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda5
UUID=a527d99a-e407-4834-a1b9-6bb83b520670 none swap sw 0 0
/dev/hdc /media/cdrom0 auto users,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 <mount\040point> auto users,atime,auto,rw,dev,exec,suid 0 0
<device> / auto users,noauto,atime,rw,nodev,noexec,nosuid 0 0

---

### Post by bodhi.zazen on 2007-02-27
Well, these line all have errors:

/dev/hda1 <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 <mount\040point> auto users,atime,auto,rw,dev,exec,suid 0 0
<device> / auto users,noauto,atime,rw,nodev,noexec,nosuid 0 0

The first two need mount points in the second column ...

The last one needs a device ...

---

### Post by qoheleth on 2007-02-27
ok cool good advice now my problem is that I can't write to my fstab because I don't have permission how do I mount this stupid drive while in a live (kde) boot.

---

### Post by bodhi.zazen on 2007-02-28
> **qoheleth said:**
> ok cool good advice now my problem is that I can't write to my fstab because I don't have permission how do I mount this stupid drive while in a live (kde) boot.

LOL

From you previous post it appears your root partition is hda2

So, in a terminal,

```
sudo mount /dev/hda2 /mnt
sudo nano -B /mnt/etc/fstab
```

Re-write fstab ....

FYI the -B flag makes a back up just in case ;)

When you are done editing, Crtl-X to exit, type Y to save changes ...

Then reboot.

HTH

---

### Post by qoheleth on 2007-02-28
Ok cool I win thanks for the help I hope I don't crash it again, I'm still trying to get the hang of all that permission stuff.  I actually solved the problem by going through my windows boot and editing the file.

---

