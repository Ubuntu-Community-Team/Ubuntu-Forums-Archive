---
title: "Mounting mixed-content CD-OM"
date: 2007-02-13
forum: General Help
---

### Post by kwaanens on 2007-02-13
I have many audio-CDs with music videos, and have problem copying (or even viewing) the videos. The discs mount OK on insert, and I can rip the audio with Grip. Right clicking the destop icon gives me options to open or browse the CD, both of which opens Serpentine. CDs mount to /media/cdrom0, but there's nothing there after mounting the CD.
This has been a problem since, like, whenever... With Hoary, Breezy, Dapper and now Edgy for me.
How do I fix this? Thanks!

- Ketil

---

### Post by dcstar on 2007-02-13
> **kwaanens said:**
> I have many audio-CDs with music videos, and have problem copying (or even viewing) the videos. The discs mount OK on insert, and I can rip the audio with Grip. Right clicking the destop icon gives me options to open or browse the CD, both of which opens Serpentine. CDs mount to /media/cdrom0, but there's nothing there after mounting the CD.
This has been a problem since, like, whenever... With Hoary, Breezy, Dapper and now Edgy for me.
How do I fix this? Thanks!

- Ketil

I think you turn off auto-mounting (or auto-playing/launching your CD player program), and then you can mount the CD as a data disk and access the videos.

I'd say Ubuntu has to make a choice when presented a disk that is multi-format, and it defaults to choosing an audio CD.

---

### Post by kwaanens on 2007-02-14
Nope!

I tried unchecking everything on System > Settings > Removable... (both "storage" and "mutimedia")
But I misspoke in my first post. Sound-juicer opens when I try to browse a CD with audio. It mounts on the desktop as "CD-ROM Disc" (as opposed to "Audio CD" as the usual label)

This really, really sucks. Browsing AND playing mixed content CDs have been possible since Win98, at least, why is it so difficult with Ubuntu. I can't even find what controls the setting. Having sound-juicer open audio discs by default is a weird value anyway.

- Ketil

---

### Post by dcstar on 2007-02-14
> **kwaanens said:**
> Nope!

I tried unchecking everything on System > Settings > Removable... (both "storage" and "mutimedia")
But I misspoke in my first post. Sound-juicer opens when I try to browse a CD with audio. It mounts on the desktop as "CD-ROM Disc" (as opposed to "Audio CD" as the usual label)

This really, really sucks. Browsing AND playing mixed content CDs have been possible since Win98, at least, why is it so difficult with Ubuntu. I can't even find what controls the setting. Having sound-juicer open audio discs by default is a weird value anyway.

- Ketil

The application for that is listed in the default applications in the relevant System-Preferences menu item, you can change it to whatever you want (or turn it off).

---

### Post by kwaanens on 2007-02-15
Really?
There are two relevant entries:
System > Preferences > Removable storage and media
Changing this does nothing, as posted before.

System > Preferences > Default apps (or whatever it is in English)
This changes only which terminal to use, which browser and which e-mail app.

So I'm still stuck...

- Ketil

---

### Post by darkmaster on 2007-02-16
I've got a similar problem, no one seems intentioned to answer my question. Your problem is simple to solve, aniway. 

I need to mount a MIXED CD exactly as it is, not only one part of it, the entire disc, as you can do in damned windows. Your problem is simply solved by:

mount -t iso9660 -o ro /dev/cdrm /media/cdrom0

Then, if you open the cdrom0 folder, you'll find immediatly the data you are looking for...

But, my problem is different. I don't wanna have to choose beetwen data and audio! I need the disc to be exaclty as it is. Also, if I try to mount an .iso mixed image file, Ubuntu gives me back a mount error:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

That's my main post for this problem I've got:

[http://www.ubuntuforums.org/showthread.php?t=362487&highlight=mixed](http://www.ubuntuforums.org/showthread.php?t=362487&highlight=mixed)

If anyone can help me it would be really appreciated. I'd be happy even with a windows program mounting the image correctly to run under wine.

---

