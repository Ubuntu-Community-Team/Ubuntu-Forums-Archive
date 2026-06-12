---
title: "Nicotine freezes"
date: 2006-07-15
forum: General Help
---

### Post by LTBookman on 2006-07-15
Hello, I can't start Nicotine (and, of course, have tried reinstalling). It freezes right after I try to start it. Trying through the console I get the following errors:

  self.hbox141.pack_start(self.vbox97, gtk.TRUE, gtk.FALSE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1577: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.vbox91.pack_start(self.hbox141, gtk.TRUE, gtk.TRUE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1579: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.hbox146 = gtk.HBox(gtk.FALSE, 0)

[About a hundred variations of that same error] 

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 146, in ?
    app = frame.MainApp(config)
  File "/usr/lib/site-python/pynicotine/gtkgui/frame.py", line 933, in __init__
    self.frame = testwin(config)
  File "/usr/lib/site-python/pynicotine/gtkgui/frame.py", line 246, in __init__
    if self.np.config.needConfig():
  File "/usr/lib/site-python/pynicotine/config.py", line 83, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 100, in iteritems
    for k in self:
  File "/usr/lib/python2.4/UserDict.py", line 87, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.4/shelve.py", line 98, in keys
    return self.dict.keys()
  File "/usr/lib/python2.4/bsddb/__init__.py", line 244, in keys
    return self.db.keys()
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

Any ideas how to fix this? TIA.

---

### Post by prkfriryce on 2006-07-16
same problem here. Anyone with some answers?

---

### Post by spockrock on 2006-07-16
What version of nicotine are you using, this thread has the latest version of it, it works really well.

[http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine](http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine)

---

### Post by userundefine on 2006-07-16
Have you tried the .deb?

---

### Post by prkfriryce on 2006-07-17
> **userundefine said:**
> Have you tried the .deb?

1.2.2

> **spockrock said:**
> What version of nicotine are you using, this thread has the latest version of it, it works really well.

[http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine](http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine)


My original debug messages were in that thread. I will try the latest 1.2.3 when i get back to mi casa.

---

### Post by prkfriryce on 2006-07-18
ahh... 1.2.3 gives the same error messages

---

### Post by prkfriryce on 2006-07-18
ok, so i traced the debug back to the pynicotine dir and looked at what config.py was trying to do. I rm my local '.nicotine' directory, reinstalled,  and i'm back in business! If you run multiple instances of nicotine, be careful of overlapping the configurations!! :-#

---

### Post by LTBookman on 2006-07-19
> **prkfriryce said:**
> I rm my local '.nicotine' directory

LOL, that worked for me too. I had looked for such a folder and, now wonder how comes, couldn't find it.

Thank you all.

---

### Post by prkfriryce on 2006-07-19
> **LTBookman said:**
> LOL, that worked for me too. I had looked for such a folder and, now wonder how comes, couldn't find it.

Thank you all.

i've made identical '.nicotine' directories and just used the '-c' option to point to the configuration i needed to load. [img]http://www.sicktracks.com/forums/images/smilies/mean.gif[/img]

---

