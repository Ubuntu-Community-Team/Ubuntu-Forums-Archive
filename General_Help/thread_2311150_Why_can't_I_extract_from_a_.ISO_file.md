---
title: "Why can't I extract from a .ISO file?"
date: 2016-01-25
forum: General Help
---

### Post by kkk5 on 2016-01-25
I've been trying to run this file, but I can't even get it mounted in my system!

How can I mount, run, and install this .iso file?

---

### Post by Vladlenin5000 on 2016-01-25
You probably can't because it's Windows software.

---

### Post by Yellow Pasque on 2016-01-25
> I've been trying to run this file, but I can't even get it mounted in my system!

What happens when you try to mount it? Your screenshot just shows what happens when you tried to open it in an archiver program, probably by (double-)clicking it in the file manager.

> **Vladlenin5000 said:**
> You probably can't because it's Windows software.

False. It's an .iso of a DVD-ROM, so it's probably a UDF format. The OP sees the error because he is trying to open it with an archiver program that (uses a backend that) doesn't read UDF: [https://github.com/libarchive/libarchive/issues/138](https://github.com/libarchive/libarchive/issues/138)
The fact that it contains Windows software is irrelevant. If one mounts the .iso, s/he should be able to install/run the software through wine.

Please do some basic reading on .iso before trying to offer advice on it:
[https://en.wikipedia.org/wiki/ISO_image](https://en.wikipedia.org/wiki/ISO_image)
[https://en.wikipedia.org/wiki/Universal_Disk_Format](https://en.wikipedia.org/wiki/Universal_Disk_Format)

---

