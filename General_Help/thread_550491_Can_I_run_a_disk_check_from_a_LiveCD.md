---
title: "Can I run a disk check from a LiveCD?"
date: 2007-09-13
forum: General Help
---

### Post by Stan_1936 on 2007-09-13
Can I run a disk check from an Ubuntu or Xubuntu Live CD?  I have an em,pty disk which I want to test using fdisk(? don't know the exact name or anything else about it) BEFORE installing Fluxbuntu on it.  I would remoev my current HD and connect the master cable to this other HD, insert the Live-CD and would at this stage like to run a disk check because the HD (Maxtor 12 GB 5400 RPM) is quite old.

---

### Post by Stan_1936 on 2007-09-13
I've gone through the forums before posting this thread.  Anyone?

---

### Post by bodhi.zazen on 2007-09-14
Yes, that is the preferred way ...

sudo fsck /dev/hdxy (or /dev/sdxy)

You should run fsck with the partition unmounted.

---

### Post by Stan_1936 on 2007-09-14
ok, whoa, that went right over the top of me....

Do I need more than one line or several?  I don't know how to mont/unmount so haven't done it.

---

### Post by bodhi.zazen on 2007-09-14
> **Stan_1936 said:**
> ok, whoa, that went right over the top of me....

Do I need more than one line or several?  I don't know how to mont/unmount so haven't done it.

LOL, sorry about that, my fault. I assumed from your post you would understand geek speak :redface:

Boot the live CD

Open a terminal ...

Make sure the partition you want to check is not mounted. I do this by entering the following command in the terminal :

```
mount
```

If you do not know basic linux partitioning terminology , see this link : 

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

If the drive is listed in the mount command you will need to unmount it.

```
sudo umount /dev/xxxx
```where xxxx is device (partition) to unmount, the one you want to check.

Then enter ```
sudo fsck /dev/xxxx
``` in the terminal, again dev/xxxx is the partition/drive to check

---

### Post by Stan_1936 on 2007-09-15
Thanks, that should do it.

---

