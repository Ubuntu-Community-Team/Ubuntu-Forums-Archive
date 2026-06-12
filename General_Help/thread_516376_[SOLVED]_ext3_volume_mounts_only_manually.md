---
title: "[SOLVED] ext3 volume mounts only manually"
date: 2007-08-03
forum: General Help
---

### Post by badmadrabbit on 2007-08-03
Hello!

I have a ext3 volume that won't mount on boot up. If I mount it manually with 
sudo mount -t ext3 /dev/sda1 /home/jona/Music 
it works perfectly without problems. I put it in /etc/fstab (and if I remember it right it worked the first few times) but when I boot it doesn't mount.
Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /boot           ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc5       /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc6       /media/hdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /home/jona/Music ext3   defaults,user_xattr                0       1
/dev/sda5       /home           ext3    defaults,user_xattr                0       1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

And a part of the log /var/log/message ... I thought maybe it could help (this is the log when I mount it myself...I didn't find any other log containing possible interesting) information:
```
 Aug  3 10:00:42 jona-desktop kernel: [ 2884.398652] kjournald starting.  Commit interval 5 seconds
Aug  3 10:00:42 jona-desktop kernel: [ 2884.401084] EXT3 FS on sda1, internal journal
Aug  3 10:00:42 jona-desktop kernel: [ 2884.401484] EXT3-fs: mounted filesystem with ordered data mode.
```

Has anyone an idea what I could do? It's not a big problem, but **really** annoying ;-)

Cheers,
Jona

---

### Post by heimo on 2007-08-03
When you mount it manually, does it have extended attributes enabled? Is that valid option for ext3 filesystem? Have you tried passing that option when mounting manually?

---

### Post by merlinus on 2007-08-03
This may be off the wall, but...

try moving its line in /etc/fstab above all the ntfs partition lines, which should be at the end of the file, according to specs at ntfs-3g.org.

-merlin

---

### Post by badmadrabbit on 2007-08-03
@heimo
Where can I look up whether they are enabled or not?

@merlinus
I am going to try it, thanks. 

/dev/sda6 works fine by the way.

Jona

---

### Post by badmadrabbit on 2007-08-03
I just looked at my /etc/fstab one more time and I think I spotted the fault.

In /etc/fstab I mounted /home/jona/Music right before I even mounted /home.

No miracle that it didn't worked after all :-) But thanks for your all help, I probably wouldn't have found the flaw in months. 

@merlin 
Are the ntfs partition lines supposed to be at the very end, even after the cdrom lines?

---

### Post by merlinus on 2007-08-03
No, only after ext3 (or other linux filesystems).

-merlin

---

### Post by heimo on 2007-08-03
> **badmadrabbit said:**
> 
In /etc/fstab I mounted /home/jona/Music right before I even mounted /home.


Good catch, merlinus and badmadrabbit. I too should've noticed that, because I've done the same mistake. Yeah, you need to have a mount point and mount things near filesystem root first. :) Good you got it working.

---

