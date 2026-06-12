---
title: "Feisty corrupts UDF file system on DVD-RAM"
date: 2007-06-01
forum: General Help
---

### Post by timetunnel on 2007-06-01
I've been quite happy using DVD-RAM on my IBM R52 laptop for over a year now for backup purposes. However, since upgrading from Edgy to Feisty I have serious problems with it. It seems like Feisty (or maybe the latest kernel) creates corrupted folders in the UDF file system.

One issue, which I already reported in Launchpad, is that some folders aren't recognized as folders anymore and are reported as "unknown type" in Nautilus or with "ls -l":
[https://bugs.launchpad.net/ubuntu/+bug/117328](https://bugs.launchpad.net/ubuntu/+bug/117328)

Today another problem showed up: one folder on a DVD-RAM has a "Circular directory structure", like this:
"/media/cdrom0/bla/bla/bla/bla"
You can always cd down into the next "bla" folder, endlessly, but there should be only "/media/cdrom0/bla" actually.

Trying to remove this folder results in the error ""Circular directory structure" and it's will not be removed.

Since there is no fsck.udf, how can I fix this? Moreover, I can't rely on my backups anymore, because this happens on almost every disc I use. 

Any help is deeply appreciated.
Jens

---

### Post by mrgod on 2007-06-20
I got the same issue, but with a USB HDD.  There is a program named testdisk, but I havenæt tried it, cause I'm scared to loose data.

---

### Post by timetunnel on 2007-06-20
seems like [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") doesn't support UDF - so it wouldn't be useful anyway, if you use UDF on DVD-RAM (which I do)

---

