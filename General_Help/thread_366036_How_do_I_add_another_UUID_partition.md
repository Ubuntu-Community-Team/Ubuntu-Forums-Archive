---
title: "How do I add another UUID partition?"
date: 2007-02-20
forum: General Help
---

### Post by daller on 2007-02-20
Hi there,

What's with the UUID-thing?

I have my harddisk partitioned into 2 main partitions.

One holds this feisty installation (30GB) and the other 10GB is from an old edgy installation (Didn't think I would be using feisty for my main platform yet, but I do now!)

How do I access the data on the other partition? (I think it's hda1, but I can't figure out how to setup fstab now with all this UUID...)

/etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=be980683-fe99-4d45-a2b2-1da6324113bb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=1a4fb6aa-39c4-408b-b114-f67d4a2e787e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
~
~

```

**Update: The disk seems to be recognized as /dev/sda, but that doesn't help me with the UUID thing...**

Thank you!

---

### Post by taurus on 2007-02-20
You don't have to use UUID in /etc/fstab if you don't want to.  You can use the actual device like /dev/hda1 if you wish and in fact, I think you should use the /dev/hda1 because if you reformat your /dev/hda1, then you would have a new UUID but /dev/hda1 is still /dev/hda1.

```

/dev/hda1   /media/hda1   ext3   defaults   0   1
```
Then, create a new mount point for it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```

---

### Post by daller on 2007-02-20
Thank you! - Now I have the data copied to my main partition!

Any tips on how to format it the easiest/best way?

Furthermore, can I delete one of the swap partitions? (see the attachment!)

---

### Post by taurus on 2007-02-20
You can reformat it (ext3) again with

```
sudo mke2fs -j /dev/sda1
(If /dev/sda1 is what you want to reformat.)
```

---

### Post by daller on 2007-02-20
> **taurus said:**
> You can reformat it (ext3) again with

```
sudo mke2fs -j /dev/sda1
(If /dev/sda1 is what you want to reformat.)
```

...but that will not change the UUID of the remaining partitions, and screw up my fstab references?

---

### Post by jimbob on 2007-02-20
If you really want to do the UUID thing, I think entering:  vol_id -u <your partition here> will give it to you.

ie: for my zip drive ...

vol_id -u /dev/sdb1

returns the UUID.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by taurus on 2007-02-20
> **daller said:**
> ...but that will not change the UUID of the remaining partitions, and screw up my fstab references?

It only changes the UUID of the partition that you reformat, nothing else.  That's why I recommend you use the actual device instead of the UUID so you don't have to worry about this stuff in /etc/fstab.

---

### Post by daller on 2007-02-20
...and as far as I recall, grub is installed on that partition...

...How do I check that?

---

