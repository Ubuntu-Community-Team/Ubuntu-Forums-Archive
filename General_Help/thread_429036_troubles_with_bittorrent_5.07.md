---
title: "troubles with bittorrent 5.07"
date: 2007-04-30
forum: General Help
---

### Post by groggyboy on 2007-04-30
I've been trying to get the [latest version of BitTorrent]("http://www.bittorrent.com/download") running on my Feisty box.

Neither the .deb version nor the source-compiled version will run for me.  In both cases, I get this error:```
groggyboy@ono-sendai:~/Desktop/BitTorrent-5.0.7$ bittorrent
>>> unable to setrlimit  not allowed to raise maximum limit
Traceback (most recent call last):
  File "/usr/bin/bittorrent", line 183, in ?
    from BitTorrent.GUI_wx.DownloadManager import MainLoop
  File "/usr/lib/python2.4/site-packages/BitTorrent/GUI_wx/__init__.py", line 29, in ?
    import wx
ImportError: No module named wx

```

Anyone?

---

