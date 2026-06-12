---
title: "Partition Scheme - new Install"
date: 2008-05-18
forum: General Help
---

### Post by hamhock on 2008-05-18
I'm about to install Ubuntu 64-bit.  Should I create an additional /data partition for very large files created by Virtualbox and mythTV?

/swap
/
/home
/data  (VDI's and mpg's)

If this is ok, would I create the /data during install?  Is ext3 ok for /data?

Thanks,

---

### Post by Ocxic on 2008-05-18
it's perfectly acceptable. I personally use XFS for my filesystem it handles large files very well, and i think it performs better then EXT3

---

