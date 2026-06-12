---
title: "No disk space = can't log in"
date: 2007-05-05
forum: General Help
---

### Post by klato on 2007-05-05
So I just booted up today and I tried logging in, but every time I entered my user name and password, I would just get another login screen.  Someone mentioned how they were using the system yesterday and got a notice how there was no disk space left.  So I deleted some stuff, and voila, I can log in again.  Just thought I'd mention it to everyone if they run into this problem.

Cheers!

---

### Post by VernerVonTux on 2007-05-05
I'm had the same problem here: [http://ubuntuforums.org/showthread.php?p=2598234#post2598234](http://ubuntuforums.org/showthread.php?p=2598234#post2598234)
I too deleted files to be able to log in again ;however, this only works as long as I don't run a kdeinit process (any kde application) otherwise my hard drive fills up again with unlocatable files. Did you find the files that filled your hard drive, or did you delete some personal data to make room, also, could you run an fsck check on your computer, what results does that yield? Deleting some files yielded results for a while but all of a sudden after my last shutdown, my 2.9 gigs of free space don't seem to be free anymore because I can't log on again either.

---

### Post by klato on 2007-05-05
I just deleted some personal files to be able to log in.  Also, I'm running gnome, so I'm not too sure about kdeinit.

I tried running fsck, but it said that it may cause severe damage to a mounted filesystem if I do it, so I said no.

---

### Post by bapoumba on 2007-05-05
```
df -H
```
will tell you which partitions are full (or almost full now).

```
sudo aptitude clean
```
will make some room on your root (/) partition.
Check also your trash.

---

