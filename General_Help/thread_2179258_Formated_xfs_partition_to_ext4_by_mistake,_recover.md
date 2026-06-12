---
title: "Formated xfs partition to ext4 by mistake, recover?"
date: 2013-10-07
forum: General Help
---

### Post by Yahoé on 2013-10-07
Hi, I formatted a xfs partition by mistake to ext4. Can this be undone and the data recovered?

Regards.

---

### Post by Cope57 on 2013-10-09
There are services which can do this for you, but the price of doing so is quite high.  Just search for data recovery and find sites such as this one [http://www.universeinfosoft.com/](http://www.universeinfosoft.com/) 


They may be able to help, but then again nothing is certain.

---

### Post by btindie on 2013-10-09
As long as you haven't written to the disk, you may have some luck with TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Yahoé on 2013-10-09
Actually, I did not chose to have the partition reformatted during installation, I just kept the default partition type ext4, when I should have selected xfs, so I do not know if the installer reformatted it or just changed the partition type. I'll give a try to testdisk since I now have cloned the drive with dd.

---

### Post by Yahoé on 2013-10-12
Testdisk couldn't do anything. I was able to use photorec to restore the data, music files mostly, and using Musicbrainz Picard I was able to then rename the restored file automatically.

---

