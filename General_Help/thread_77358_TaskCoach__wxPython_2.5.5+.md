---
title: "TaskCoach / wxPython 2.5.5+"
date: 2005-10-16
forum: General Help
---

### Post by harryf on 2005-10-16
Trying to get TaskCoach ([http://members.chello.nl/f.niessink/](http://members.chello.nl/f.niessink/)) to run under Ubuntu (Breezy).

It needs wxPython 2.5.5+ which I've managed to install but now hit the following error message running TaskCoach (or anything else that uses wxPython).

> 
ImportError: /usr/lib/wxPython-2.5.5.1-gtk2-unicode/lib/libwx_gtk2ud-2.5.so.5: undefined symbol: pango_x_get_context


Here's what I did;

First uninstalled wxPython 2.5.3 (the most recent with Breezy).

Then;

```

apt-get install libgtk2.0-dev freeglut3-dev python2.4-dev
wget http://puzzle.dl.sourceforge.net/sourceforge/wxpython/wxPython2.5-2.5.5.1-1_py2.3.src.rpm
sudo rpmbuild --rebuild --define 'pyver 2.4' wxPython2.5-2.5.5.1-1_py2.3.src.rpm
cd /usr/src/rpm/RPMS/i386/
sudo dpkg -i wxpython-common-gtk2-unicode_2.5.5.1-2_i386.deb
sudo dpkg -i wxpython2.5-gtk2-unicode_2.5.5.1-2_i386.deb
sudo dpkg -i wxpython2.5-devel-gtk2-unicode_2.5.5.1-2_i386.deb

```

(Also tried the same with the most recent wxPython 2.6 release - same problem)

Version of Pango is the default Breezy version 1.0.0. Any ideas how to fix this?

Otherwise, perhaps a workaround would be to build the ASCII version of wxPython (to avoid Pango). But how?

Many thanks.

---

### Post by harryf on 2005-11-05
OK - fixed thanks to Ron Lee's debian package of 2.6 now being available.

Be warned if you-re looking for wxpython the package name is now python-wxgtk.

To fix my problem just;

```

sudo apt-get install python-wxgtk2.6

```

---

