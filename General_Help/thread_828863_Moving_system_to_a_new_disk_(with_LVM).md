---
title: "Moving system to a new disk (with LVM)?"
date: 2008-06-14
forum: General Help
---

### Post by cerbero on 2008-06-14
Hi,
I'm trying to find some information on how to move a complete system to a new (bigger) disk, when my system is on an LVM volume, but haven't been able to find anything directly applicable to my situation.

Right now, everything is on an old 120 GB IDE drive. I just got a left over 250 GB SATA drive that I would like to use in stead, but I don't want to have to reinstall everything.

The old disk has a 250 MB ext3 boot partition, a 3 GB swap partition, and an LVM partition takes up the rest of the drive. The LVM partition constitutes a volume called root in an array called Ubuntu, and the root volume has an ext3 file system.

What would be the easiest way to move all of this to the new drive? Can I clone the drive with dd and it would just work? If so, would it be possible to grow the LVM volume and its file system to make use of the new drive?

---

### Post by logos34 on 2008-06-14
Clonezilla supports LVM2, I believe.

dd might work, OTH you might have problems with fdisk and the like reporting correct disk info

---

### Post by rraj.be on 2008-06-14
Hope this helps you fine.

```
[[COLOR="Red"]http://pittman.ws/articles/howto/partimage.html[/COLOR]]("http://pittman.ws/articles/howto/partimage.html")
```

Advantages of partimage are

1-->Fast

2-->reilable

3-->[COLOR="Blue"]clones only used memory thus saving your backup space[/COLOR]

---

### Post by logos34 on 2008-06-14
> **rraj.be said:**
> Hope this helps you fine.

```
[[COLOR="Red"]http://pittman.ws/articles/howto/partimage.html[/COLOR]]("http://pittman.ws/articles/howto/partimage.html")
```


So, Partimage supports LVM?

---

### Post by rraj.be on 2008-06-14
I havnt tried yet, but my friend used that.

---

### Post by keithweddell on 2009-04-02
From what I have read, Clonezilla uses dd to copy LVM partitions so copies "empty space" as well as data. I think Partimage can do the same when used from the command line but doesn't recognise LVM at all from the GUI.  I have not yet found a good solution for this so would be grateful for suggestions.

Keith

---

### Post by bbiandov on 2009-07-17
> **keithweddell said:**
> From what I have read, Clonezilla uses dd to copy LVM partitions so copies "empty space" as well as data. I think Partimage can do the same when used from the command line but doesn't recognise LVM at all from the GUI.  I have not yet found a good solution for this so would be grateful for suggestions.

Keith

So long story short, there is NO way to move LVM from one disk (say disk that is about to fail) to another and one has to basically cp individual files and directories once the new disk is up and running, with OS installed and configured

What a pain that is? If I knew I would have NEVER allowed setup to use LVMs when initially setting up the system

Oh well, good leasson

---

### Post by jerome1232 on 2009-07-17
This should be easy with LVM actually. And it can be done while the system is running without rebooting and etc...

 I've done it a few times before I can't recall what the EXACT commands would be but,

You add the new physical volume to the volume group and use pvmove I think it was to move all logical volumes from one physical volume to another physical volume. 

You can then remove the old physical volume from the Volume group and viola.

The difficult part is if you need to move that boot partition you might have to use cloning to do that.

edit: Check out the man pages for lvm, pvmove, vgextend, vgreduce, These are the tools you will need to use.

Edit2: Actually I think I recall it all pretty well, if you could show what your pv's and vg's look like I can help you do the migration.

To show me what your volumes look like

```
sudo vgdisplay
sudo pvdisplay
```

---

