---
title: "CDROM mounted as hdc"
date: 2004-11-24
forum: General Help
---

### Post by praxim on 2004-11-24
Hi,

  I just installed Ubuntu via a Knoppix CD.  When automounting CDs, I get them at /media/hdc instead of /media/cdrom (causing the desktop icon to be hdc and not the CD volume, and also coming up with some rather strange CD contents).  Here's fstab:

```

proc       /proc       proc   defaults            0 0
/dev/fd0   /mnt/floppy auto   user,noauto,exec,sync,umask=000    0 0
/dev/cdrom /mnt/cdrom  auto   user,noauto,exec,ro 0 0
/dev/hda1 none swap defaults 0 0
/dev/hda2 / reiserfs defaults 0 0

```

Creating /media/cdrom does me no good.  Changing /mnt/ to /media/ also does nothing.  Anyone know what's up?

---

### Post by p!=f on 2004-11-24
Can you explain why did you install Ubuntu via Knoppix when you can use pretty easy Ubuntu installer?
Dist-upgrading from Knoppix installation is not a good idea (TM).

> 
/dev/cdrom /mnt/cdrom  auto   user,noauto,exec,ro 0 0

My entry says
```

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```
Perhaps replacing /dev/cdrom with /dev/hdc could do the trick.

---

### Post by praxim on 2004-11-24
Thanks, changing the fstab entry worked.  I should've thought of that in the first place...   :oops: 

I didn't dist-upgrade a Knoppix install.  I did a direct install using Knoppix as described in the wiki because I'm visiting my little brother, who hosed his (previously Windows-running) PC.  We didn't have any blank CDs on hand, but did have network access and a Knoppix CD from earlier, so it looked like a good way to go.  I'm quite pleased with the distribution, though I'm sure he'll throw Windows back on at the first chance he gets.

---

### Post by p!=f on 2004-11-24
[QUOTE=praxim]
I didn't dist-upgrade a Knoppix install.  I did a direct install using Knoppix as described in the wiki because I'm visiting my little brother, who hosed his (previously Windows-running) PC.  We didn't have any blank CDs on hand, but did have network access and a Knoppix CD from earlier, so it looked like a good way to go.  I'm quite pleased with the distribution, though I'm sure he'll throw Windows back on at the first chance he gets.[/QUOTE]
Oops, my bad. :)

---

