---
title: "mtink shows 8 cartridges instead of 6 and all ink levels are zero Epson R200"
date: 2014-06-11
forum: General Help
---

### Post by philinux on 2014-06-11
Anyone else seeing similar or have a fix?

[https://bugs.launchpad.net/ubuntu/+source/mtink/+bug/1328578](https://bugs.launchpad.net/ubuntu/+source/mtink/+bug/1328578)

This is on 14.04

---

### Post by Mark Phelps on 2014-06-11
Did you add the module usblp to /etc/modules ?  That has been needed in recent Ubuntu versions for mtink to work.

I'm using it on 14.04 with an Epson Artisan -- and it works fine.  Used in in 12.04 on an Epson R220 and it worked OK there, too.

---

### Post by philinux on 2014-06-11
> **Mark Phelps said:**
> Did you add the module usblp to /etc/modules ?  That has been needed in recent Ubuntu versions for mtink to work.

I'm using it on 14.04 with an Epson Artisan -- and it works fine.  Used in in 12.04 on an Epson R220 and it worked OK there, too.

Hi yes, I used my fix here but it still shows 8 inks instead of 6 and still has 0%.

ink -p usb 

works though

---

### Post by philinux on 2014-06-13
Bump. Anyone else using mtink/

---

