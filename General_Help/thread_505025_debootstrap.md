---
title: "debootstrap"
date: 2007-07-19
forum: General Help
---

### Post by box2 on 2007-07-19
i've tried running:
$ debootstrap sid /home/testchroot [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/)

i've also tried running it with comparable options to install feisty instead of sid.  the same problem for both: it gets to a point then says:
W: Failure trying to run: chroot /home/level/tes mount -t proc proc /proc
and quits out.

so i try the command on my own and apparently the problem is that the mount command isn't inside of the chroot environment... so i copy my /bin and /lib into /home/testchroot and run the debootstrap command again.  this time it gets further but fails again on another command not being inside of the chroot (this one being located in /sbin, so i copy that directory into my testchroot also).  i run the command again and lo, it works!

i look at my /home/testchroot directory and... hello?  the only files in there are the ones i copied myself and a few useless files in etc/, debootstrap/, and var/....

i thought this command was supposed to move an entire workable environment into a directory?  seems i did all the moving on my own...  i don't know what the hell all that retrieving and validating packages crap was during the debootstrap... it was moving files to maybe nowhere at all?

---

### Post by tbroderick on 2007-07-21
Haven't really used debootstrap, but you might want to take a look at this;

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

---

