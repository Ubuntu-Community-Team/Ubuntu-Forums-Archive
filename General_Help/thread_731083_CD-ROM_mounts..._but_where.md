---
title: "CD-ROM mounts... but where?"
date: 2008-03-21
forum: General Help
---

### Post by ibuclaw on 2008-03-21
Hi, I can't figure out where my Audio CD-ROMs mounts.

Ubuntu recognises it and mounts the device, and I can look at the music tracks through Sound juicer, yet conventional music players such as Totem and VLC can't seem to find it.

Looked in my /media/cdrom0 folder, nothing. It's empty.

Gnome's link to the "Audio Disc" says:
>  "cdda:///dev/scd0" is not a valid location. 
fstab showed this:
```
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 
```
Tried these commands and got the following responses:
```

umount /dev/scd0
       umount: /dev/scd0 is not mounted (according to mtab)

mount /dev/scd0
       mount: block device /dev/scd0 is write-protected, mounting read-only
       mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail
       [ 3016.256000] end_request: I/O error, dev sr0, sector 816736
       [ 3016.256000] end_request: I/O error, dev sr0, sector 817976
       [ 3016.264000] end_request: I/O error, dev sr0, sector 816952
       [ 3016.264000] end_request: I/O error, dev sr0, sector 816728
       [ 3016.264000] end_request: I/O error, dev sr0, sector 1248
       [ 3016.268000] end_request: I/O error, dev sr0, sector 1024
       [ 3016.268000] UDF-fs: No partition found (1)
       [ 3016.308000] end_request: I/O error, dev sr0, sector 64
       [ 3016.308000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

And yet normal CD/DVD/DVD-Audios mount and load normally...

Hmmm, bizarre. I'm sure I've been able to do this before...

Any help would be appreciated.

Iain

---

### Post by ibuclaw on 2008-03-21
bump

---

### Post by billgoldberg on 2008-03-21
I never use cd's or dvd's so but I guess their icon should be on the desktop or in nautilus. You should be able to access the songs that way.

---

### Post by fenian on 2008-03-21
I think audio cds mount to cdda://scd0/

> yet conventional music players such as Totem and VLC can't seem to find it.
 
I would say those are both conventional VIDEO players and are not really that good for playing music

---

### Post by mc4man on 2008-03-21
cd's don't mount per se because they're not a filesystem - won't be in /media/cdrom0  You should be able to access from dev/. Did you try from terminal vlc cdda:///dev/scd0
i'm not big on music players so i use that command in the mutlimedia tab to autorun cd's with vlc -works fine

---

### Post by ibuclaw on 2008-03-21
> **mc4man said:**
> cd's don't mount per se because they're not a filesystem - won't be in /media/cdrom0  You should be able to access from dev/. Did you try from terminal vlc cdda:///dev/scd0
i'm not big on music players so i use that command in the mutlimedia tab to autorun cd's with vlc -works fine

Okay, audio now plays. That's cool.

So, no actual viewing of the CD-ROM drive is possible are you saying then?

Regards

---

### Post by mc4man on 2008-03-21
> So, no actual viewing of the CD-ROM drive is possible are you saying then
not really - if you try to browse the folder you'll just open up soundjuicer   (in the case of cd's)

---

