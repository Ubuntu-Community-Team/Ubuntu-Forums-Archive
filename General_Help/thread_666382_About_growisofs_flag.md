---
title: "About growisofs flag"
date: 2008-01-13
forum: General Help
---

### Post by satimis on 2008-01-13
Hi folks,


Ubuntu 7.10
growisofs version 7.0.1


Please advise which flag to be up for checking the data after burning DVD+RW.  I can't figure it out on reading "man"

TIA


B.R.
satimis

---

### Post by erpo on 2008-01-13
growisofs doesn't appear to have a flag that does this. You'll have to use an external program like md5sum to compare the burned files with the originals. Take note of the -c option to md5sum, which can make checking large numbers of files much more fun.

---

### Post by satimis on 2008-01-15
> **erpo said:**
> growisofs doesn't appear to have a flag that does this. You'll have to use an external program like md5sum to compare the burned files with the originals. Take note of the -c option to md5sum, which can make checking large numbers of files much more fun.
Thanks for your advice.


Whether you meant running;

# md5sum -c Tarball.tar.bz2

and 

# mount /dev/dvd /mnt
# md5sum -c /mnt


Then compare the results.


satimis

---

