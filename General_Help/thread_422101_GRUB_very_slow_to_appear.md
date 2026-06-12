---
title: "GRUB very slow to appear"
date: 2007-04-24
forum: General Help
---

### Post by Pox on 2007-04-24
I think I rebooted in the middle of grub starting or something yesterday, because GRUB has become excessively slow - it's taking about 2 minutes to show after POST, and it used to be about 1 second.

I've tried reinstalling with

```

grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

```

but to no avail - still just as slow.  (Yes, hda1 is my boot partition, and yes it's installed on the MBR.)

Does anyone have any ideas how to fix it?  As far as I'm aware the above should entirely overwrite the MBR, so I have no clue what's happening :(

Any help is appreciated, TIA.

/EDIT: btw, if it's any help, I'm on xubuntu edgy.

---

### Post by Pox on 2007-04-25
Anyone have any ideas? Does grub keep a log I can look at, and is there a more complete way of overwriting the MBR with a new copy?

---

