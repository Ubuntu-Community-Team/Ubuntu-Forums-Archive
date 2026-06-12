---
title: "OpenOffice crash"
date: 2004-11-01
forum: General Help
---

### Post by vulpes on 2004-11-01
On warty, my openoffice.org always crashes with "An unrecoverable error has occured." It used to work, so apparently some update has killed it. I tried using a clean setup (rm ~/.openoffice, etc.), and different user accounts and it still happens.  I to have universe and multiverse enabled, and also  [http://www.getsweaaa.com/~tseng/ubuntu/debs](http://www.getsweaaa.com/~tseng/ubuntu/debs)

Any suggestions?

---

### Post by vulpes on 2004-11-01
Found the answer in Debian Sarge forums.

In /etc/openoffice/openoffice.conf, uncomment this line:

export SAL_DISABLE_CUPS=1

---

