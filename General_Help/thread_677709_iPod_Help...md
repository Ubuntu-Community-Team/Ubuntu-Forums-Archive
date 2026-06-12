---
title: "iPod Help.."
date: 2008-01-25
forum: General Help
---

### Post by spaceship.rodeo on 2008-01-25
I posted this [here](http://ubuntuforums.org/showthread.php?p=4194130#post4194130), but that hasn't seemed to garner much response, so maybe here it will do better?

Anyway, I need help with mounting my iPod to my computer.  Whenever I plug it in, it gives me this error:
Cannot mount volume
mount_point cannot contain the following character: newline, G_DIR_SEPARATOR (usually /)
and I don't know what to do to fix it.  It seems fairly simple, though.  But if anyone can help me change the mount point or ipod name or whatever is wrong here so I can at least update the damn thing, it would be a great help.

I'm running Gutsy with a 5th Gen, 30gb iPod, if it makes any difference.

---

### Post by kidders on 2008-01-26
Hi there,

Your Ubuntu is probably trying to use your iPod's filesystem label as the name for its mount point in /media, but the label could be something like "My/iPod" or
"My
iPod"

I would suggest ...

Ignore the warning & mount your iPod manually, just so you can see it still works, and nothing bad has happened. Be sure to substitute the correct /dev node name for "sda1"...```
# mkdir -p /mnt/ipod
# mount /dev/sda1 !$
```While it's mounted, note the filesystem type (eg by typing **mount**)

Dismount it, and re-label the filesystem, using the appropriate utility, eg ...```
# umount /mnt/ipod && rm -R /mnt/ipod
# mlabel c:
```The next time you plug in your iPod, it should behave itself.

---

