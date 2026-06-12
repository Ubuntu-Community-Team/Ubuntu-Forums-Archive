---
title: "DVD not working"
date: 2007-09-20
forum: General Help
---

### Post by joebanana on 2007-09-20
Pls help. I burned a DVD (verbarim DVD+R) at work with Vista burning tool, that that comes with the explorer but its not working on my faisty fawn.

When Ubuntu tries autorun.
```
Invalid mount option when attempting to mount the volume 'UDF Volume'.
```

My fstab
```

/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I tried auto insted of udf,iso9660 but didnt wok. Also tried to maunt manually...

```
rok@rok-desktop:~$ sudo mount -t udf /dev/cdrom /media/cdrom
Password:
mount: blo&#269;na enota /dev/cdrom je zaš&#269;itena pred pisanjem, priklapljamo v bralnem na&#269;inu
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg|tail
```

rok@rok-desktop:~$ dmesg|tail
[  150.832282] Unable to identify CD-ROM format.
[  198.778149] Unable to identify CD-ROM format.
[  211.017150] Unable to identify CD-ROM format.
[  262.203501] Unable to identify CD-ROM format.
[  271.168275] Unable to identify CD-ROM format.
[  803.817302] hdc: request sense failure: status=0x51 { DriveReady SeekComplete Error }
[  803.817312] hdc: request sense failure: error=0x04 { AbortedCommand }
[ 3836.184457] Unable to identify CD-ROM format.
[ 3861.612384] Unable to identify CD-ROM format.
[ 4017.968664] UDF-fs: No fileset found

```

pls write anything that might help... I searched a lot of web found nothing useful.

---

### Post by ddrichardson on 2007-09-21
Does it work in windows? This'll let you know if its a bad burn.

What if you mount it as iso9660```

sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

---

### Post by Irihapeti on 2007-09-21
Have you burned the DVD as standard "mastered session" format, or as UDF which allows you to use it rather like a floppy? Vista's burner, from memory, defaults to the UDF version in some circumstances. (Sorry, it's several weeks since I burned a DVD in Vista - that's why I'm vague.) If it's a UDF DVD, then Ubuntu won't read it unless you install udftools. 

I still haven't managed to get udftools to read the UDF DVDs I burned in Vista (and which I can mount in a friend's XP computer) so someone else would need to help with that.

Irihapeti

---

