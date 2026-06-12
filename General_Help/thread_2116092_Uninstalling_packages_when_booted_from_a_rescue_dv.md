---
title: "Uninstalling packages when booted from a rescue dvd/USB stick"
date: 2013-02-14
forum: General Help
---

### Post by ArlieS on 2013-02-14
I recently had an unpleasant experience with graphics on a ubuntu 12.10 system. To make a long story short, the workaround required either removing or installing additional packages - and the system wasn't cooperative about giving me a non-graphical shell, particularly if I also wanted networking to be available. (I could get a "single user" [pre-networking] shell.) 

I was able to boot from DVD and mount my disks. But tools like apt-get [and the GUI equivalents] don't appear to have a way for me to specify a path to the target file system. (They don't even tell me the paths to the databases they are using.) So any changes I made would affect only the transient ubuntu installation I got from selecting "try ubuntu" when booted off ubuntu installation media, not the broken installation I had on my hard disk. 

I eventually managed to get a usable shell booted from disk, and solved THIS particular problem.  But I'm left looking for a general solution to add to my tool kit. Given a ubuntu system which won't come all the way up due to the presence or absence of some package, HOW does one change the packages installed on it?

---

### Post by kanikilu on 2013-02-15
I think you can do this by booting with a live disc/USB, mounting the partition with the broken system on it, and then changing root (chroot).

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Some more good information at the Arch wiki:

[https://wiki.archlinux.org/index.php/Change_Root](https://wiki.archlinux.org/index.php/Change_Root)

I haven't actually done this myself, so can't really help beyond pointing you to the docs...

---

### Post by Bufeu on 2013-02-15
Just use *chroot* to change root folder (*/*).
E.g. ```
sudo chroot /media/hard_drive
```This command will set */media/hard_drive* as "root folder" (*/*).

---

