---
title: "iSeries Access - 5250 emulator"
date: 2007-12-12
forum: General Help
---

### Post by badccg on 2007-12-12
hi everyone,

I'm new to linux .. so please pardon the newby in me.  I would like to install iSeries Access from IBM, which is a 5250 emulator.  I've read that the package is dependent on openmotif 2.*   

How or where do I install this package for ubuntu?



CC

---

### Post by jflaker on 2007-12-12
I am still playing with this and if I ever get time, I will get it to work.

You can download it from ibm:
[http://www-03.ibm.com/systems/i/software/access/linux/index.html](http://www-03.ibm.com/systems/i/software/access/linux/index.html)
This is supposed to be all the feature that the windows version has.......it looks like a work in progress...so stay tuned

This is an RPM package which Debian can not install.  You need to make a .DEB from it using ALIEN.

Once you have converted the package, it will install it to /opt/ibm/iSeriesAccess.  No application menu items will be install, just the programs.
The binaries to run are in /opt/ibm/iSeriesAccess/bin


I need to contact IBM on this, but if you have time to play around, you can probably get it to work......you can create links on the desktop for quick access.  IBM can be contacted @ 1-800-IBM-SERV

Let me know if you have luck in getting it working.

---

