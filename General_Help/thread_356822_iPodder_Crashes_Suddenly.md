---
title: "iPodder Crashes Suddenly"
date: 2007-02-08
forum: General Help
---

### Post by abbot on 2007-02-08
I've been using iPodder for quite a long time to download podcasts & vidcasts with no problems.  I always have it running in the background when my computer is on.  I just noticed that it wasn't running for some reason.  when i try to start the program it crashes pretty much immediately after the splash window comes up.  this is the output from the terminal.

adam@adam:~$ ipodder
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Traceback (most recent call last):
  File "/usr/share/ipodder/iPodderGui.py", line 3531, in ?
    main()
  File "/usr/share/ipodder/iPodderGui.py", line 3525, in main
    myApp = iPodderGui(ipodder)
  File "/usr/share/ipodder/iPodderGui.py", line 590, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/ipodder/iPodderGui.py", line 1460, in OnInit
    self.PopulateDownloadsTab()
  File "/usr/share/ipodder/iPodderGui.py", line 3220, in PopulateDownloadsTab
    encinfolist = self.ipodder.state['tmp_downloads']
  File "/usr/share/ipodder/ipodder/state.py", line 176, in __getitem__
    return self.__shelf[key]
  File "bsddb/dbshelve.py", line 107, in __getitem__
UnicodeDecodeError: 'utf8' codec can't decode byte 0xa7 in position 38: unexpected code byte

---

### Post by abbot on 2007-02-17
no one has any ideas?  if not can someone please suggest a different podcast/vidcast aggregator that i can use?

---

### Post by andrej_ on 2008-01-18
I got exactly the same problem, since about two days... is there anyone who can help?

---

