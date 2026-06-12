---
title: "HD Space Problem"
date: 2007-01-12
forum: General Help
---

### Post by Edward The Bonobo on 2007-01-12
I have Ubuntu installed on an old 4GB HD.  The default installation should only need approx 2GB.  With Dapper, I had just over 1GB free.  With Edgy, I now have only 150MD.  I have a few extra packages (not many!).  I tried a Complete Removal on a couple (eg Gnucash)...but this **lost** an extra 20MB!

Any ideas on how I can free up HD space?  What can I afford to be without?  I only need about 1GB total on my installation disk.

---

### Post by tribaal on 2007-01-12
After you remove packages, make sure you issue a "apt-get clean" command: otherwise, the downloaded packages are kept in cache on the HDD.

Maybe you will find it frees up the space difference?

Hope this helps

- trib'

---

### Post by Edward The Bonobo on 2007-01-12
Excellent!  I did that and now I've got >1.1GB free.  I guess there were probably some other things cached.

Thanks.

---

