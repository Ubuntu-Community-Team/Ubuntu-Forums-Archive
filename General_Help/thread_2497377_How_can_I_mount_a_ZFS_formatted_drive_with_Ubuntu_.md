---
title: "How can I mount a ZFS formatted drive with Ubuntu 24.04 LIVE"
date: 2024-05-02
forum: General Help
---

### Post by couzin2000 on 2024-05-02
I have a ZFS-formatted drive from another linux distro. I'm trying to access the files inside, but I'm using Ubuntu 24.04 from a USB key as a LIVE version - uninstalled.

Can anybody explain how I would be able to get the packages running in this context so I can read the contents of the ZFS disk? I've scoured the web for this and nothing seems to exist on the subject. I need to be able to get the files off the disk onto another system on my local LAN.

---

### Post by MAFoElffen on 2024-05-04
First you need to teach the Live Image Environment how to speak ZFS
```

sudo su -
apt install -y zfsutils-linux

```
Then find out what ZFS pools can be imported
```

zpool export -a
zpool import

```
Doing that command will list all pools that are not already imported. Lets say the pool you wanted to use was MyPool. Then to import it
```

zpool import -f -N -R /mnt MyPool

```
Repeat that for any other pools that you want to mount...

Then list the dataset structure
```

zfs list

```
Let's say your recognise the base dataset structure as something like
```

zfs list
MyPool/DATA/ubuntu_2404

```
Then you would do
```

zfs mount MyPool/DATA/ubuntu_2404
zfs mount -a

```
You should now be able to access any files within that pool's filesystem, under the /mnt folder.

Note thatthose instructions are just to access the files, not to repiar an OS within that, which would then take chrooting into that filesystem.

---

### Post by couzin2000 on 2024-05-04
I've installed a persistent 24.04 on a USB drive. and installed [FONT=Courier New]zfsutils-linux[/FONT].
Problem is, looks like the pool cannot be seen. Ubuntu is not mounting the drive by default, and if I run [FONT=Courier New]gparted[/FONT] I can see the drive and the volume but [FONT=Courier New]gparted[/FONT] cannot read that volume. Since the volume was created on a different computer altogether, I'm not sure the system is actually importing whatever volume is on that disk. Any ideas as to what I can do to make the USB install see it?

---

### Post by MAFoElffen on 2024-05-05
You have installed zfsutils-linux persistently, so I will skip that part from now on. In many things I do with ZFS, all it's utils are at root level, so I often start out by doing
```

sudo su -

```
instead of having to preface everything with sudo.

ZFS is like LVM2... They are both Volume Managers. You load the drivers for them, and they see their relatable structures. With 'them' you mount the respective storage containers, not the filesytems of a partition. So yes, GParted see's the partition that a ZFS pool or LVM PV is on, but does not understand a ZFS filesystem with a ZFS pool > ZFS filesystem dataset, or for that matter an LVM PV > VG > LV. Both as Volume Managers, and can span across many partitions and disks.

So... when, in the above instructions, you do (as root):
```

zpool import

```
Does it see anything?

If not, then what does say when you do (as root)
```

zdb

```
Note, that the commands I gave you temporarily mount the pool under the /mnt folder. If you wanted to mount it elsewhere permanently, and you have made the folder tags where you want it to mount to... Tell me, and I will suggest the commands for that.

---

### Post by couzin2000 on 2024-05-06
STUPENDOUS.
Looks as though these commands are valid cross-platform.
I was trying to list the volume but I was from the wrong disk (long story but I was looking at my parity drive).
I had installed Ubuntu and ZFS on the key, looks like everything was working, but reading the wrong drive wasn't helping at all.
I rebooted and installed OpenZFS on my Windows 10 machine. Turns out, when I connected the right drive, I was able to import the pool and mount it. I currently have access to my contents.

I cannot thank you enough for your step by step guide. I really appreciate this!

---

### Post by #&amp;thj^% on 2024-05-06
MAFoElffen is a keeper for sure.

If this is solved could you please mark it as SOLVED to help others as well. :)
Enjoy

---

### Post by MAFoElffen on 2024-05-06
Glad it all worked out.

Yes. ZFS is it's own animal, thankfully. Very powerful. Very robust, flexible and adaptable. 

If you ever have any question on or about ZFS, do not be hesitant to ask 1fallen or I.

We both tend to try to stretch it to it's limits, just to see what is possible, and how to fix it when we do blow it up. LOL. That seems to entertain both of us figuring that out.

Also keep this link handy: [https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin)

I tend to try to document things I know, to document it, on how to do things ZFS. That is the place I choose to document ZFS diagnostics and repairs... That way I can just post the link to the answer instead of having to retype it all over, and over again. LOL. I'm getting on in years. This stuff needs to live on past me. It's just the right thing to do.

---

### Post by fragglebliss on 2024-10-09
> **MAFoElffen said:**
> First you need to teach the Live Image Environment how to speak ZFS
```

sudo su -
apt install -y zfsutils-linux

```
Then find out what ZFS pools can be imported
```

zpool export -a
zpool import

```
Doing that command will list all pools that are not already imported. Lets say the pool you wanted to use was MyPool. Then to import it
```

zpool import -f -N -R /mnt MyPool

```
Repeat that for any other pools that you want to mount...

Then list the dataset structure
```

zfs list

```
Let's say your recognise the base dataset structure as something like
```

zfs list
MyPool/DATA/ubuntu_2404

```
Then you would do
```

zfs mount MyPool/DATA/ubuntu_2404
zfs mount -a

```
You should now be able to access any files within that pool's filesystem, under the /mnt folder.

Note that those instructions are just to access the files, not to repiar an OS within that, which would then take chrooting into that filesystem.

I just want to give a shout-out to you, and thank you for this post.

I just had a computer meltdown and the contents of the drive was in a ZFS pool.

Considering this was my first experience attempting to retrieve data from a ZFS pool, I was going in blind.

This thread proved vital to me successfully retrieving all of the data from the pool.

I honestly can't thank you enough! :)

---

