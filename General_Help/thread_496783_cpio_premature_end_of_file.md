---
title: "cpio premature end of file"
date: 2007-07-09
forum: General Help
---

### Post by cmnorton on 2007-07-09
I have looked at other posts in Ubuntu forums. My problem seems different, because it is directly realted to cpio, not trying to install another product. So this is not a deliberate duplicate post.

I am trying to install an Informix sdk. It installs on Red Hat 9, RHEL (3 and 4), and Fedora 6. To unpack the data and scripts, I use cpio -icdumvB < csdk.cpi. However, on Ubuntu LTS 6, it fails with premature end of file. 

I would appreciate any suggestions as to how to correct this. 

Thanks
cmn

---

### Post by cmnorton on 2007-07-09
The answer to this is remove -c from the cpio command line. I could extract the file, but a scipt that I downloaded also needed -c removed as well.

---

