---
title: "Deluge-torrent open URL problem"
date: 2007-10-29
forum: General Help
---

### Post by jasonxh on 2007-10-29
I can not open urls from deluge correctly. For instance, when I click the link in about dialog, firefox tries to open a page with url "file:///home/jason/%22http://deluge-torrent.org%22" instead of just "http://deluge-torrent.org", which supposedly gives me file not found error. It's the same thing when using torrent search plugin in deluge.

I have tried  0.5.0, 0.5.5 and 0.5.6, all the same thing. BTW I'm running feisty. Anyone shares  the same problem?

---

### Post by jasonxh on 2007-10-29
Never mind, I got a solution from deluge forum. It is a firefox bug
[https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/83974]("https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/83974")

---

### Post by Ramo666 on 2007-11-01
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Traceback (most recent call last):
  File "/usr/bin/deluge", line 121, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 109, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 262, in __init__
    self.state = pickle.load(pkl_file)
EOFError

help please!!!!!!!!!!!!!!!!!!!!!!!!!! reinstallation have no result!!!!!!!!!!!:confused:

---

