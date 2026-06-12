---
title: "wxPython error"
date: 2007-11-13
forum: General Help
---

### Post by sovereign_soul on 2007-11-13
Am I the only one with this problem ? can't find much info abt this even on the great google!

everytime I (or any application e.g. wxglade) tries to use wxpython .. the following error appears.

/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so: symbol _ZTV14wxGraphicsPath, version WXU_2.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference

I have absolutely no clue as to how to correct this. This issue has been bugging me since abt 2wks..so plz help !!!!!

---

### Post by sovereign_soul on 2007-11-14
What happened to the "ubuntu" spirit guys ? Not even a single response ?:confused:

---

### Post by dakevman on 2007-12-09
I have exactly the same problem... i really dunno whats happning.... plz help!

---

### Post by sgleason on 2008-07-15
I've got this problem a swell. I saw these posts from November 2007, dose anybody have a clue whats going on with this error?

If I go into ipython and type "import wx" I get exactly the same error. I'm running Gutsy and other Python packages seem to work fine (SciPy etc). wxWidgets is installed and works fine for C++ projects.

Just checking to see if anyone has solved this over the last ~9 months.

-Scott

---

### Post by sgleason on 2008-07-15
I've reinstalled python-wxgtk2.8 python-wxtools python-wxaddons wx2.8-i18n as  suggested on this wiki [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

but it still does not work.  I get a different error:

ImportError: /usr/local/lib/libwx_gtk2u_core-2.8.so.o: version 'WXU_2.8.8' not found (required by /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_code_.so)

-Scott

---

