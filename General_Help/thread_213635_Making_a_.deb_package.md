---
title: "Making a .deb package"
date: 2006-07-11
forum: General Help
---

### Post by slugkilla on 2006-07-11
I am compiling bzflag-2.0.8 right now and want to make a .deb package instead of just makeinstalling it. I want this package to beable to replace the one currantly installed so that when an offical one comes out, I won't have any problems. How would I go about doing this?

Edit: Nevermind, the compile failed and I'm not skilled/devoted enough to fix the issue. Thanks anyway.

---

### Post by HAARP on 2006-07-11
I'll tell you anyway:
Get checkinstall (repos) and use **sudo checkinstall** instead of **sudo make install**

---

### Post by cptnapalm on 2006-07-11
According to this page, [http://www.falkotimme.com/howtos/checkinstall](http://www.falkotimme.com/howtos/checkinstall) what you should do, instead of "make install" is:

checkinstall -D make install

I need to check this out as an easy to use .deb maker would be handy.

So the full proceedure, assuming the source conforms to standards is:

[B]cd /wherever/the/directory/of/the/source/is
./configure (maybe add -h to see options)
make
sudo checkinstall -D make install[/B]

That is if I read correctly.

---

### Post by hanzomon4 on 2006-07-11
checkinstall all ways fails when try it

---

### Post by slugkilla on 2006-07-11
Thanks for the info because I might need to do this for other packages later on.

---

### Post by go_beep_yourself on 2007-10-29
Checkinstall does not work for wxDownloader. How can a deb be created of it.

[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

---

