---
title: "Trying to install a deb file for Zebra (which seems to be a database)"
date: 2014-01-26
forum: General Help
---

### Post by Timmoore001 on 2014-01-26
I've downloaded:-

libidzebra-2.0_2.0.55-1indexdata_amd64.deb  libidzebra-2.0

and trying to get Ubuntu 12.04 64 bit to accept it.

No luck so far at the command level or Ubuntu Software Centre

Any thoughts on what I should be doing ?

A puzzled,

Tim

---

### Post by TheFu on 2014-01-26
Google found these instructions [http://www.indexdata.com/zebra/doc/installation-debian.html](http://www.indexdata.com/zebra/doc/installation-debian.html)
which has a PPA - much preferable to trying a raw .deb file installation.

I haven't tried Zebra nor the install instructions above.

Note they do not pre-build AMD64 packages, just i686, so if you need 64-bit versions, be prepared to build it yourself and maintain the packages and all the dependencies manually forever.  That applies to installing the .deb file too.

Could you please post the exact commands used plus any output, wrapped in "code" tags?  Without seeing exactly the commands enter and the output, we're stuck on our end.  I've never found any use for software center.

---

### Post by Timmoore001 on 2014-01-27
Many thanks for most useful link.

I'll post more details when I've digested that.

Tim

---

