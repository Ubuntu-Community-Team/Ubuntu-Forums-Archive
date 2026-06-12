---
title: "NTFS Partition Woes"
date: 2006-10-22
forum: General Help
---

### Post by leveliv on 2006-10-22
hi i recently installed 5.10 just cause I had it lying around and I wanted a change. (dont worry I am upgrading to 6.06, Nov 1st due to Bandwidth restrictions) anyways I recently installed and ubuntu recognized my NTFS partition right off the bat, but when I click on the 'hda1' icon on my desktop (GNOME) I get a dialogue that says:
```
You do not have the right permissions to access this content.
``` or something. now with that partition (NTFS) my username I use to do my everyday thing is Administrator and it is passworded, does that do anything? also here is how I have it mounted: ```
/dev/hda1     /media/windows  ntfs nls=utf8, umask=0000 0     0
```

I used to have the umask set at 0222 but I wanted read/write not just read. any help is appreciated. thanks --Chris

---

### Post by Jussi Kukkonen on 2006-10-23
Do you know that NTFS write access is, if not experimental, at least not doable by default? I strongly advice against trying NTFS writing with programs and drivers from last year, unless you know very well what you are doing -- the risk to your data is real.

---

### Post by leveliv on 2006-10-23
well okay I will change it to umask=0222 that still doesnt solve my problem LOL

---

### Post by PriceChild on 2006-10-23
use```
/dev/hda1       /media/windows        ntfs    nls=utf8,umask=0222        0       0
```(you had an extra space)

There are ntfs write guides out there on the forums in the HOWTOs section, but they're not reccomended and may cause massive data loss.

---

### Post by givré on 2006-10-23
> **PriceChild said:**
> use[code]and may cause massive data loss.
You should test it price, you would be really surprise.
Anyway, read/write is quite stable right now with an upcoming driver : ntfs-3g.
And it will *not* cause massive data loss.
But it's still a beta soft.

---

### Post by leveliv on 2006-10-24
So all I need to do is take this: ```
/dev/hda1       /media/windows        ntfs    nls=utf8,umask=0222        0       0
``` and put it in my fstab, and there I go? all that because I had an extra space haha :mad:  that makes me feel dumb..haha thanks

---

