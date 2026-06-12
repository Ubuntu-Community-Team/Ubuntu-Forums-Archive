---
title: "Delete Paritions"
date: 2008-07-02
forum: General Help
---

### Post by d34d10gic on 2008-07-02
Anyone know how I can delete my Windows and my other Ubuntu partitions? I'm satisfied with only this one, but I can't restart.

---

### Post by soccerboy on 2008-07-02
please elaborate on what you mean by you can't restart.

---

### Post by d34d10gic on 2008-07-02
If I restart, I won't be able to start up Ubuntu again due to the "Busy Box" error.

It kind of just means I can't use the liveCD.

---

### Post by bodhi.zazen on 2008-07-02
> **d34d10gic said:**
> Anyone know how I can delete my Windows and my other Ubuntu partitions? I'm satisfied with only this one, but I can't restart.

You can use gparted. You need to install it first. You can not delete a partition that is in use ( / or swap), for that you need to use a live CD.

If you are wanting to wipe the hard drive, DBAN

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by d34d10gic on 2008-07-03
Doesn't work, there is a key next to the ones I want to delete that says that it is locked.

---

### Post by bodhi.zazen on 2008-07-03
> **d34d10gic said:**
> Doesn't work, there is a key next to the ones I want to delete that says that it is locked.

You need to :

1. Run gparted as root.

2. Best to run from a live CD.

3. Unmount the partition first (this will remove the lock). From the live CD the most likely culprit is swap. You can unmount partitions and swap from either the command line or gparted.

From the command line list your mounted partitions with:

```
mount
```

Then :

```
sudo umount /dev/sdxy
```

or, for swap

```
sudo swapoff /dev/sdxy
```

replace "sdxy" with the partition you want to unmount.

---

