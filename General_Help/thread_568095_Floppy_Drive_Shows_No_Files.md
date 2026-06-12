---
title: "Floppy Drive Shows No Files"
date: 2007-10-05
forum: General Help
---

### Post by Greasyfingers on 2007-10-05
I'm having trouble with my floppy drive. I can mount it, but no files are visible on any disk I insert. If I try and save a file to a floppy I get a message saying the disk is full. The drive seems to make no attempt to physically scan the disk.

I'm dual booting with Windows, and can access files on floppies from there, so it's not a hardware problem, and it was working OK a few weeks ago. I've tried changing the line in fstab from

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

to

```
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
```

but to no effect. Anyone help?

---

### Post by chrisxp on 2007-10-06
i had the same problem, but with my cdrom.. turns out it was the driver, ubuntu chose a generic driver, which obviously didnt work.. try looking for a driver your floppy drive and if you cant find one post the make/model and we'll try our best to find one :)

---

### Post by Greasyfingers on 2007-10-07
Well, I'm not sure what was going on there, but the floppy drive is working OK now. It *may* have been an issue with VirtualBox, which was running in the background when I had the problems; it seemed for a while that I could mount but not read a floppy until I shut down the virtual machine which was running. Still experimenting with VB, so not at all sure that I wasn't just being a dunce. Thanks anyway.

---

