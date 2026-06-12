---
title: "Deleted all root certs in firefox"
date: 2007-02-26
forum: General Help
---

### Post by kasetty on 2007-02-26
I accidentally deleted all the root certificate authorities that come standard with firefox installation in Ubuntu 6.10.  How do I get the certs back.  I tried removing firefox and then installing firefox but it is of no help.  Where does firefox stores it root certs (cert8.db seems to contain personal certs which were accepted but not all the default root certs).

  Would appreciate any pointers on this.

thanks,
Kasetty

---

### Post by zanglang on 2007-02-27
Not sure about restoring certificates, but you can probably try deleting (or move, if you'd rather not lose everything) your firefox conf folder in ~/.mozilla/firefox, ~/mozilla-firefox or something similar, depending on your installation.

---

