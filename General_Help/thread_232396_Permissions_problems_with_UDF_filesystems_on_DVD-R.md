---
title: "Permissions problems with UDF filesystems on DVD-RAM"
date: 2006-08-08
forum: General Help
---

### Post by mjgumbley on 2006-08-08
Hi, I'm using an external USB DVD rewriter (LG GSA-2164D) with DVD-RAM media and UDF (pre-formatted at the factory) filesystems.

I boot, log in, and insert a blank DVD-RAM. It automounts under /media/dvdrecorder, and I drag some files to it. I find the drive under "Computer", Eject it. For some reason I have to repeat this before the disk ejects.

However, after re-inserting the disk, it mounts, and then Nautilus tells me I have insufficient permissions to read the disk. /media/dvdrecorder is owned by root:root, and has 0770 permissions.

(If I su - root, I can see it fine with ls).

I'm logged on as me, not root, I created the files on the media initially. Why can't I now see them automatically?

Regards,
Matt

---

### Post by mjgumbley on 2006-08-08
FWIW, I have dvd+rw-tools 5.21.4.10.8-4ubuntu1 installed.

---

