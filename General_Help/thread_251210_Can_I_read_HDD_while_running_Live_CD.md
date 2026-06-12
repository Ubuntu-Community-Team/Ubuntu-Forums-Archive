---
title: "Can I read HDD while running Live CD?"
date: 2006-09-05
forum: General Help
---

### Post by jkaines on 2006-09-05
I have a 'dead' Packard-Bell laptop - a victim of Dapper upgrade.
It boots up fine from a Live CD (ver 5.04).

Can I mount the HDD to get some data off? If so, how?
I don't necessarily want to repair the old installation, I just want to get at my  personal files.

---

### Post by Zalbor on 2006-09-05
Of course you can. Something like
```
sudo mkdir /disk
sudo mount /dev/hda1 /disk
```
should work, supposing that your partition is hda1.
But are you sure that's the only way to do it? I find it strange that updating can cause such a problem that wouldn't be solvable.

---

### Post by jkaines on 2006-09-05
Zalbor, you are a gentleman (I think) and a scholar - you've done it. (Very supprised that there were no security issues).

I'm not a linux user (yet) just trying to help a guy who has a year's worth of writing of a book on this laptop that got screwed-up when he did the latest upgrade. (Don't ask about backups! - maybe he'll do them from now on).

From what I can see it looks as though the update changed the device name for the HDD and so can't find it when booting-up.

It would be nice if I could get the HDD to boot again, but if it's going to take too much time (especialy yours) perhaps I'll get him to do a re-install from scratch.

Thanx for you help

---

### Post by jkaines on 2006-09-05
Upgrade problem.

By the way when I try to boot normally from the HDD it eventually ends up with . . . . .


ALERT! /dev/hda1 does not exist. Dropping to a shell!
BUSYBOX . . . .etc
/bin/sh: can't access tty: job control turned off
# _


Is this easily fixed?

---

### Post by bjohnson1102 on 2006-09-05
this is easily fixed...You need to boot to the live cd as before, mount your volumes, then edit the PathTo/menu.lst (which on ubuntu I believe it to be /etc/boot/grub/menu.lst) and update the location of your kernel.  Chances are you'll also need to edit your /etc/fstab file to update any additional mount points.  hope this helps.

Brad

---

### Post by jkaines on 2006-09-05
Brad,

Thanx for your help but those paths apear not to exist.

You're talking to a 'think' non-linux user remember.

Thanx anyway.

---

### Post by revoltism on 2006-10-11
if it's a s-ata hdd it should be /dev/sda1 instead. u can check this with the live cd what the mount points are.

I'm pretty much newbee myself so i'm not sure if it help's.

---

### Post by CatKiller on 2006-10-11
> **jkaines said:**
> Thanx for your help but those paths apear not to exist.

I think that should be /boot/grub/menu.lst

Or /disk/boot/grub/menu.lst if you used the mount point described earlier.

---

