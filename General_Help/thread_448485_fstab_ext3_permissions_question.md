---
title: "fstab ext3 permissions question"
date: 2007-05-19
forum: General Help
---

### Post by jonnymccullagh on 2007-05-19
I have my home partition on a sepearate hard drive to my main system so I can upgrade but keep my settings and files intact. In my fstab I have:
/dev/hdb1 	/home 		ext3 	nodev,nosuid 	0 	2

However, I am beginning to think this is not completely correct. I often get padlock signs on file icons indicating file permission problems.

Is there something I need in place of nodev,nosuid which I can put to indicate who owns the mount?
thanks in advance,
jonny

---

### Post by taurus on 2007-05-19
What's wrong with using

```
/dev/hdb1    /home    ext3   defaults    0    2
```

---

### Post by jreinis on 2008-07-14
man mount >>

nouser Forbid an ordinary (i.e., non-root) user to mount the file system.  This is the **default**.

so we are,ordinary users, won't have permission to mount /in GUI/ write etc on own hard disks.

---

