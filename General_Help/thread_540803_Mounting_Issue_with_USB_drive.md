---
title: "Mounting Issue with USB drive"
date: 2007-09-02
forum: General Help
---

### Post by 3370318 on 2007-09-02
Hello, I've got a question concerning where Ubuntu 7.04 keeps its rules regarding removable devices such as usb disks.  In particular, I have an external usb hard drive that I would like to mount for mythtv usage, but I cannot seem to override whatever default rules Ubuntu applies.  I've created a rather high priority udev entry with the following parameters:

```
BUS=="usb", SYSFS{product}=="ST94811U2-RK", KERNEL=="sd?1", NAME="usbdisk", GROUP="mythtv", OWNER="myuser", MODE="0000"
```

and have set up an entry in fstab as follows (121 is mythtv's group):

```
#USBDISK
/dev/usbdisk  /media/usb_disk  vfat  defaults,utf8,umask=000,gid=121   0   0
```

yet for some reason unknown to me, none of those options seems to be applied and instead, I always get the following result:

```
drwx------ 31 myuser root    32768 1969-12-31 18:00 usb_disk
```

I suspect that there exists some rule that I just don't know about that Ubuntu defaults to for removable media.  Does anybody know how I can disregard this rule and instead force Ubuntu to mount my drive as I'd like?

Thanks

---

### Post by merlinus on 2007-09-02
Does the drive show up with this command:

```

sudo fdisk -l

```

-merlin

---

### Post by 3370318 on 2007-09-02
yes, it shows up with fdisk with the dev entry /dev/sdb1 (as would be expected).

I don't really have any issues accessing the drive... if I were just using it as my regular user, I would have no problem with the mounting procedure.  The problem occurs when I try to use it with mythtv as I need that drive to be assigned to the mythtv group.  Though I've set everything that I can think of to force the drive to be mounted for mythtv, Ubuntu seems to simply disregard these rules and instead assign it to the root group with permissions set for that group only.

---

### Post by 3370318 on 2007-09-03
Ok this I feel kinda stupid for not doing this earlier, but rebooting retained all of my changes.  I thought that restarting udev and unmounting/remounting would make everything work, but I guess I was wrong.  Anyway, I've got my mythdrive now.

---

### Post by Vin¢ on 2007-09-05
I've been having sporadic trouble w/ my USB drive (Fat32 since I bounce back / forth between Kubuntu, XP & OSX.

6.06.1 would let me change permissions on the drive, but 7.04 won't.

Any hints?  Different FS perhaps?

Vin¢

---

### Post by brundles on 2007-09-11
OK, now I'm confused.

I made the same changes as outlined above by 3370318 but don't get the same behaviour.

Forcing a different name than sda1 shows up in /dev, but not from a df -l (although sd?? doesn't show up) and it's not mountable.

Leaving the name change out and just altering the permissions lets it show up in a df -l and it mounts but it's still not accessible:
```

From udev (rules.d/40-permissions.rules):
BUS=="usb", KERNEL=="sd??", SYSFS{product}=="USB DISK 28X", GROUP="htpc", OWNER="mythtv", MODE="0664"

From /dev:
brw-rw-r-- l mythtv htpc      8,   1 Sep 11 13:54 sda1

From df -l:
/dev/sda1              1007328    337120    670208  34% /media/UDISK 28X

```

Adding the following to rules.d/20-names.rules changes the name in /dev but then it doesn't mount at all.
```

BUS=="usb", KERNEL=="sd??", SYSFS{product}=="USB DISK 28X", NAME="udisk"

And the fstab change:
/dev/udisk   /media/udisk   vfat   defaults,utf8,umask=007,gid=46 0 0

```

I've tried with both the group ID that matches the group assigned in the permissions.rules file and also with that one (46 - the plugdev group) with no luck either way.

Very confused :confused:

*Edit:* Nevermind - it would help if I created the mount point first!

---

