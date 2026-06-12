---
title: "Backported Qt4 packages"
date: 2005-07-28
forum: General Help
---

### Post by dand on 2005-07-28
Hi,

I couldn't find any Qt4 packages for Hoary, so I backported them from Sid. I thought I'd share them, in case anyone else finds them useful.

1. Add the following line in /etc/sources.list :
deb [http://people.tmlug.ro/dand/ubuntu/](http://people.tmlug.ro/dand/ubuntu/) hoary-backports-dand main

2. Run:
aptitude update
aptitude install xlibmesa-glu-dev qt4-dev-tools qt4-doc

(you could also use apt-get instead of aptitude; read [sarge release notes](http://www.debian.org/releases/sarge/releasenotes) why aptitude is better than apt-get)

Unfortunately the packages are not signed, since I'm not familiar with signing and I'm pretty short on time... hope that's not such a big problem.

Hope it helps,
-dan

---

### Post by Octane on 2005-08-06
This is for i386, right?

---

