---
title: "e2fs errors + coredump"
date: 2007-08-05
forum: General Help
---

### Post by svensandberg on 2007-08-05
[ cross-posted as a bug report: [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/129395](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/129395) ]

I have an external USB disk with an ext3 filesystem. I ran e2fsck on it. It reported thousands of errors in the file system (uploaded to [http://user.it.uu.se/~svens/e2fsck-output](http://user.it.uu.se/~svens/e2fsck-output) (85 kB)). Then (during pass 2), it printed the following:

XXX should never happen!!!
Aborted (core dumped)

I could not find any core file. I ran `e2fsck -c -c' to do a surface test, but everything was ok. Then I ran e2fsck again, and it started giving the same type of errors as the first time I ran it, only for different inodes.

I uploaded the complete output from dumpe2fs to [http://user.it.uu.se/~svens/dumpe2fs-output](http://user.it.uu.se/~svens/dumpe2fs-output) (937
kB).

My disk is called Samsung Xtend AdStore XAS3UI500. Before I ran the first test, I (accidentally) unplugged the disk without first unmounting it, several times.

What do you suggest me to do to rescue my files?

---

