---
title: "How to access Ubuntu CD packages from installed system?"
date: 2014-08-30
forum: General Help
---

### Post by aleks2 on 2014-08-30
The problem is, most of packages are hidden inside `/casper/filesystem.squashfs`.
The utility `apt-cdrom` that was meant for adding CDROM to sources.list doesn't help with that, so only several packages from `/pool` are accessible.
How to access all packages from CDROM with APT?? No `squashfs-tools`, no graphical environment on system (only core minimum).
Come on, such a basic operation which was very easy to do with Debian now became pain in a$s...

---

### Post by 3rdalbum on 2014-08-30
You're using the wrong CD. You need to use the Alternate CD, that contains the raw packages.

The Desktop CD (which is the one people normally download) does not contain packages, only their installed contents.

---

### Post by aleks2 on 2014-08-30
I guessed that, but couldn't find 14.04 Alternate CD. I only see 12.04.4 Alternate CD. Is 14.04 available?
...
Just found LUbuntu Alternate CD, this will do. Thanks!

---

### Post by kansasnoob on 2014-08-30
AFAIK only Lubuntu builds the alternate images now:

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html)

---

