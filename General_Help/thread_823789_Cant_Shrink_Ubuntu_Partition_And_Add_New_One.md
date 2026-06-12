---
title: "Cant Shrink Ubuntu Partition And Add New One"
date: 2008-06-09
forum: General Help
---

### Post by Nemisis_101 on 2008-06-09
Hello,

I have a Ubuntu installation on my 60 GB Hard Drive, I have this install dual booting with Windows XP, which is on another Hard Drive. I would like to create a new 20GB NTFS partition on my Ubuntu HDD. I booted up the Live CD, went to the GParted, unmounted the /dev/sdb1 (ext3) - its 54 GB. Resized it down to 34 GB, created a new partition - 20GB NTFS clicked apply. It says it cant because of an error. I checked the details and it says -

```

check filesystem on /dev/sdb1 for errors and (if possible) fix them
       e2fsck -f -y -v /dev/sdb1
            /dev/sdb1 is mounted
            e2fsck 1.40.8 (13-Mar-2008)
            e2fsck: Cannot continue, aborting.


```

What should i do to achieve this?

Thanks,

---

### Post by drs305 on 2008-06-09
> **Nemisis_101 said:**
>  I checked the details and it says -

```

check filesystem on /dev/sdb1 for errors and (if possible) fix them
       e2fsck -f -y -v /dev/sdb1
            /dev/sdb1 is mounted
            e2fsck 1.40.8 (13-Mar-2008)
            e2fsck: Cannot continue, aborting.


```

What should i do to achieve this?

Thanks,

Just looking at the output message, have you tried unmounting /dev/sdb1 and running:
```
e2fsck -f -y -v /dev/sdb1

```

If that puts out errors, let us know what they are.

---

### Post by Gannon8 on 2008-06-09
For some odd reason, GParted mounts all unmounted partitions when it runs, but says its unmounted in the menus. Just right click on the drive icon on the desktop and select Unmount.

---

### Post by Nemisis_101 on 2008-06-09
> **drs305 said:**
> Just looking at the output message, have you tried unmounting /dev/sdb1 and running:
```
e2fsck -f -y -v /dev/sdb1

```

If that puts out errors, let us know what they are.

/dev/sdb1 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)?
[/code]

@Gannon8 - That also does not work - same error.

---

### Post by housam on 2008-06-09
try the [[COLOR="Red"]_Gparted live CD_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

---

### Post by drs305 on 2008-06-09
I agree with housam, it's probably time to switch to the GParted CD, which will ensure the parition isn't mounted. If you still want to continue the path you were on:

As to my last post, it said to **unmount** the partition and then run the command. That is important. You indicated you couldn't unmount it by right clicking and unmount.

You can try to unmount it with:
```
sudo umount /dev/sdb1
```

Then run this to make sure you don't see it mounted.
```
mount
```

Then try the e2fsck command again.

---

### Post by Nemisis_101 on 2008-06-09
That also didnt work, I will try the Live CD for Gparted now.

---

### Post by Nemisis_101 on 2008-06-09
It worked.

Thanks,

---

