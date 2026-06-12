---
title: "Automounted USB drive not in mtab?"
date: 2007-04-20
forum: General Help
---

### Post by skip27 on 2007-04-20
Strangest problem. I updated to Feisty today with just a few bumps in the road; nothing I couldn't fix, except this automounting problem. My external 160GB HD is automounting itself during bootup but isn't showing up in the mtab. If I just type 'mount' in the console, the USB drive doesn't show up. If I try 'umount <drive>' or 'pumount <drive>', I get told that the drive isn't mounted despite the fact that I can still access it through my /media path! All of its files are accessible, readable, etc. If I try to eject it through Nautilus (doesn't give me the option to unmount it), I get thrown a bunch of error messages telling me that the drive isn't mounted.

What gives? Why is Linux telling me my HD isn't mounted when it quite clearly is? The only way I can "unmount" the drive is if I physically disconnect it. Once I reconnect it, the regular udev rules work as they should and I can freely mount/unmount the drive at will.

EDIT: I found the 'unmount volume' in Nautilus, but it still reports that the volume isn't mounted despite the fact that it clearly is.

---

### Post by skip27 on 2007-04-20
Bump... does anyone have a hunch as to why Linux would be telling me that a drive isn't mounted?

---

### Post by skip27 on 2007-04-21
This is odd... when I was using Edgy, I could mount my USB drive using the UUID in /etc/fstab. The startup scripts would automatically mount the drive by using what's in /etc/fstab. In Feisty, it doesn't work. This is my /var/log/boot

```

Apr 19 16:32:55 rcS:  * Mounting local filesystems...                           mount: special device /dev/disk/by-uuid/a7afc714-cf69-4ca8-9632-50e66dafe03b does not exist
Apr 19 16:32:55 rcS:                                                     [fail]

```

Yet, when I check /dev/disk/by-uuid, it's there! Hmm... anyone have a clue? How does Feisty go about automounting volumes? And why on earth won't it show up in my mtab despite the fact that it is mounted?

EDIT: found it in dmesg...

```

[    9.392000] scsi 0:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
[    9.404000] usb-storage: device scan complete

```

At bootup, it's identifying as an authentic SCSI drive instead of a USB drive. Hmm... I'll keep stabbing at it. Is there any way to disable this? Please post your thoughts!

EDIT2: Or perhaps not, since I recall being able to mount/remount my iPod with no problems.

EDIT3: Looks like it's time for a kernel recompile... sigh...

EDIT4: <removed; see below>

---

### Post by skip27 on 2007-04-21
Fixed the problem; a kernel recompile did the trick. I am now using a vanilla build, version 2.6.20.7. dmesg is a very good indication of where to start, since it logs the activity of the KERNEL at bootup, NOT the startup scripts. So, in other words, if you encounter a problem when browsing dmesg, it's likely a kernel issue. Hence, rebuilding is almost certainly a good place to start.

---

### Post by kakubei on 2008-01-17
There seems to be a bug in Ubuntu (from way back in 6 or something) that prevents automounts from being written to mtab. There are some solutions in this Ubuntu bug forums 

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/44836](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/44836)

but they didn't work for me using Ubuntu 7.10 - the Gutsy Gibbon.

If anyone has any more ideas, they would be welcome.

---

