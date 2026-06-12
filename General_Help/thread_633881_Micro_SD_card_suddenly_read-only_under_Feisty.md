---
title: "Micro SD card suddenly read-only under Feisty"
date: 2007-12-07
forum: General Help
---

### Post by nunix on 2007-12-07
This is under 7.04

I've been using this particular micro SD card (a Kingston 2GB, just using the factory fat16 format) for a few days now, and it's been working fine. I was messing with it today, and I decided to delete the .Trash folder that had shown up on it; I figure, why the heck does it need that?

Well, since then, ubuntu claims the card is read-only. I can create, move, and delete files on both a win32 machine in the house, and my Nintendo DS (I use this for my homebrew DS programming).

1) What, exactly, happened? Linux seems to have been confused as to what the hell happened to it, and I'd kinda like a technical explaination.

2) Can this be fixed without formatting? What needs to be done?

I'm not worried about the card being trashed since, as mentioned, I can still use it, and format it if need-be... just not under linux, which is my primary platform nowadays. -.- If anyone's got some answers I'd love to hear 'em.

---

### Post by HermanAB on 2007-12-07
Check the mount parameters in /etc/fstab.

Cheers,

H.

---

### Post by nunix on 2007-12-07
I'm not really sure what I'm looking at (linux newbie), here's what /etc/fstab looks like at the moment:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=143c3cff-3c24-48d9-a989-e3e513ed4fb8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=37f844bb-46fd-4965-8ec8-5c1d893d3275 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

However, when I use df, the card comes up as /dev/sdb1, which isn't even in that file, so.. not sure.

---

### Post by nunix on 2007-12-07
Just a bump to see if someone has an answer for this before I just have to format the thing...

---

