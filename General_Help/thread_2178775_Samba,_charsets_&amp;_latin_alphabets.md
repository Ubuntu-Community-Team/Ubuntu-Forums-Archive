---
title: "Samba, charsets &amp; latin alphabets"
date: 2013-10-05
forum: General Help
---

### Post by timo_r2 on 2013-10-05
Hello!

I have a mount to a network drive using cifs:
//server/share on /mnt/mount type cifs (rw)

fstab is currently set up like this:
//server/share       /mnt/mount     cifs    rw,iocharset=iso8859-1,username=xx,password=xx,uid=xx, 0       0

locale is set to iso8859-1 for everything:
LANG=en_US.iso88591
LANGUAGE=en_US.iso88591:en

The problem is accessing files in the mount when filenames include for example latin alphabets:
timo@srr:/mnt/mount$ ls -la
ls: cannot access H_P.txt: No such file or directory
-?????????  ? ?      ?         ?            ? H_P.txt
timo@srr:/mnt/mount$ cat H_P.txt
cat: H_P.txt: No such file or directory
timo@srr:/mnt/mount$

The filesname should be HÄP.txt, although mounted on Windows it appears to be H_P.txt, but at least I can access the file.

I have tried to mount with different charsets, namely utf8, but no luck. I've also tried to script perl and use regexp with no luck. I simply can't access the file in any way using wildcards or regular expressions. It is rather annoying as I can't remove the file either. I'm using Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

Any suggestions are welcome and appreciated!

Timo

---

### Post by timo_r2 on 2013-10-09
Anyone?

---

