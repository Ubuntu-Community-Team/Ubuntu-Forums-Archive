---
title: "iPodder Lemon startup issue"
date: 2005-10-16
forum: General Help
---

### Post by attackman on 2005-10-16
Just did a fresh install of Breezy.  I attempted to install iPodder Lemon from apt and from their installer, and neither works.  I know next to nothing about Python.  Here is the command line output :

[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
USING XMMS
Traceback (most recent call last):
  File "/usr/share/ipodder/iPodderGui.py", line 3165, in ?
    main()
  File "/usr/share/ipodder/iPodderGui.py", line 3159, in main
    myApp = iPodderGui(ipodder)
  File "/usr/share/ipodder/iPodderGui.py", line 576, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/ipodder/iPodderGui.py", line 1428, in OnInit
    self.PopulateDownloadsTab()
  File "/usr/share/ipodder/iPodderGui.py", line 2864, in PopulateDownloadsTab
    encinfolist = self.ipodder.state['tmp_downloads']
  File "/usr/share/ipodder/ipodder/state.py", line 175, in __getitem__
    return self.__shelf[key]
  File "/usr/lib/python2.4/bsddb/dbshelve.py", line 107, in __getitem__
    return cPickle.loads(data)
ImportError: No module named core

I'm not really sure how to interpret that, nor have I seen the same issue posted elsewhere.  Any help would be appreciated.  Thanks all!

---

### Post by dan_linder on 2006-03-14
It's been months since you asked and I'm still getting this error with a fresh install (done the end of January).

I've tried to do a full remove of the "ipodder" package but the error returns when I re-install it.

Any Python programmers want to review the scripts to see what is going on?

Dan

---

### Post by Scunizi on 2006-03-21
I'm in the same boat with a little tweek.  I can install it from Synaptic and load it, but it won't download anything I've setup.  Works fine in XP just a struggle in Ub.:-k

---

