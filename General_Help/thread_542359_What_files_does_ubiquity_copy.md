---
title: "What files does ubiquity copy?"
date: 2007-09-03
forum: General Help
---

### Post by jokr004 on 2007-09-03
If I have a live disc with something like a modified xorg.conf or some added scripts in /usr/bin will they get copied over durring the install?

---

### Post by ruibernardo on 2007-09-04
Ubiquity makes a default installation from the DesktopCD (LiveCD).

No, ubiquity will make the default install. The xorg.conf file is created on the install process. 

All aplications are installed by dpkg. The folder /usr/bin isn't just a copy of the one in the LiveCD. All the programs are installed just the way you install them with APT (apt-get, aptitude, synaptic, adept, dpkg, etc). Ubiquity have a default list of packages that are installed on the process.

If you want to modify your live/installation CD in any way, you can try the easy way: [reconstructor]("http://http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37") or [UCK]("http://uck.sourceforge.net/") (reconstructor recommended).

You can also do it by yourself (the hard way): [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

