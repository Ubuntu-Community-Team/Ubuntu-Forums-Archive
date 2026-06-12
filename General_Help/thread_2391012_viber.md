---
title: "viber"
date: 2018-05-05
forum: General Help
---

### Post by yazdzik-k on 2018-05-05
Dear Friends,

18.04

VIber depends upon libcurl3,  but when I install viber,  it runs fine without it.

However,  it then is a broken package,  which prevents updater from running,  as well as synpatic,  or apt.

dpkg -ignore-depends=curl3 does not cure the broken package.  I need both Viber and updater to function.

All I need to do is edit the control file in the .deb,  but am not quite sure how to unpack and repack the deb,  with only that one change.

After an hour of trial and error:

(all with sudo)

dpkg-deb -x viber.deb tmpdir
dpkg-deb --control viber.deb tmpdir/DEBIAN
gedit tmpdir/DEBIAN/control
dpkg -b tmpdir viber.deb

I simply edited the control file to read libcurl4......  

I hope this helps someone else.


Best,

Martin

---

