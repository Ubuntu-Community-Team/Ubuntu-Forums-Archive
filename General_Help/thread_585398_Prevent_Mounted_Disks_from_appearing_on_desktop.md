---
title: "Prevent Mounted Disks from appearing on desktop"
date: 2007-10-21
forum: General Help
---

### Post by ray_nix on 2007-10-21
I have a hard drive containing all my media that I want mounted in my home folder.

The line in fstab is:

```
/dev/sda1       /home/user/Data        vfat    user,fmask=0177,dmask=0077,uid=1
000     0       0

```

Nothing else in fstab points to sda1 ....

I tried running gconf-editor and changing the Apps, Nautilus, Desktop option for mounted volumes to false, but it still shows up on my desktop as /home/user/Data ..

I remember that it never did it prior to Ubuntu 7.10 .. 

Anyone have any other ideas?

---

### Post by perixx on 2007-11-02
Hi ray_nix!


I had a similar problem with the mounted FD. Look at this thread...

> [http://ubuntuforums.org/showthread.php?t=223400](http://ubuntuforums.org/showthread.php?t=223400)


perixx

---

