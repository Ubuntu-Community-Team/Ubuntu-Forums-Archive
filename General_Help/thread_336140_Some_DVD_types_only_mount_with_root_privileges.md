---
title: "Some DVD types only mount with root privileges"
date: 2007-01-11
forum: General Help
---

### Post by Sporgenza on 2007-01-11
Hi,

I recently switches to Kubuntu Edgy and stumbled on a strange thing concerning DVD-automount. I have no problems reading DVD-R, I just put them in the drive, they get automounted and I can access the contents without problems. But when I try to read DVD+RW, I get the following error (KDE-DAEMON popup):
[INDENT]mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/INDENT]

A
[INDENT]dmesg | tail[/INDENT]
gives
[INDENT]Unable to identify CD-ROM format.[/INDENT]

Mounting them manually also does not work:
[INDENT]$ mount /dev/hdc /media/cdrom0
mount: only root can do that[/INDENT]
But a
[INDENT]sudo mount /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only[/INDENT]
works without problems.

A
[INDENT]dmesg | tail[/INDENT]
then gives
[INDENT]UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Datos', timestamp 2006/12/18 18:50 (103c)[/INDENT]

So briefly, it seems the automout mechanism has its problems with some DVD types. Is there a fix for this?

Some additional info:
[INDENT]$ cat /proc/version
Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)[/INDENT]

My DVD-Drive is a LG HL-DT-ST DVDRAM GSA-4163B.

Ciao

---

### Post by hal10000 on 2007-01-11
Look into your /etc/fstab and verify if your cdrom line looks like this
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto  0       0

```

The option [COLOR="Red"]user[/COLOR] makes your cd/dvd be mountable by a normal user.

---

### Post by Sporgenza on 2007-01-11
Oh, sorry I forgot to provide my fstab configuration ;(

My cdrom line looks exactly as proposed.
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I also tried it with users instead of user but with no effect.
As already described, it works this way with DVD-R but not with DVD+RW...

---

### Post by gatiba on 2007-01-17
I have the same problem in Breezy...

---

