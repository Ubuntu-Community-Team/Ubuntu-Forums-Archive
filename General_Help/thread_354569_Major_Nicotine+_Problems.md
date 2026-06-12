---
title: "Major Nicotine+ Problems"
date: 2007-02-06
forum: General Help
---

### Post by iflanery on 2007-02-06
So earlier tonight Nicotine+ hung on me while doing a search. When I tried to restart, it did load... half-way. All I got was the titlebar and a blank grey window. Switching to Nicotine+ 1.2.4 produced the same result. So, I removed both 1.2.6 and 1.2.4 from my comp. Tried reinstalling, and I got a different problem: the window loaded, but only for a split-second then was killed. So I edited my sources.list and installed Nicotine+ 1.2.6 that way. Thought it was successful until I typed in "nicotine" into my terminal window, which produced this rather nasty string of text:

> Traceback (most recent call last):
  File "/usr/bin/nicotine", line 155, in ?
    app = frame.MainApp(config, trayicon)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 1673,                                                                                                                              in __init__
    self.frame = testwin(config, trayicon)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 396,                                                                                                                              in __init__
    if self.np.config.needConfig():
  File "/usr/lib/python2.4/site-packages/pynicotine/config.py", line 87, in need                                                                                                                             Config
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("u                                                                                                                             serinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply",                                                                                                                              'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 100, in iteritems
    for k in self:
  File "/usr/lib/python2.4/UserDict.py", line 87, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.4/shelve.py", line 98, in keys
    return self.dict.keys()
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 244, in keys

bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not fou                                                                                                                             nd')


Am I pretty much SOL?

I'm using Kubuntu Edgy, b/w.

Any help would be very much appreciated.

UPDATE: It's gone back to just hanging.

---

### Post by dunomous on 2007-07-09
Please try this for your fix. It worked for me:

Delete *.db (all files ending with .db) files from your ~/.nicotine/ directory. Back up your files just in case!!

This fix was found from [here]("https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/93251").

---

