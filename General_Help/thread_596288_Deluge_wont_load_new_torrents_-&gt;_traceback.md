---
title: "Deluge wont load new torrents -&gt; traceback"
date: 2007-10-29
forum: General Help
---

### Post by SpinningAround on 2007-10-29
I can't add new torrents to deluge I started it in the terminal to see what the problem was and I did get this.

```

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1132, in add_torrent_clicked
    self.interactive_add_torrent(single)
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1076, in interactive_add_torrent
    self.interactive_add_torrent_path(torrent, path)
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1094, in interactive_add_torrent_path
    self.config.get('use_compact_storage'))
  File "/var/lib/python-support/python2.5/deluge/core.py", line 339, in add_torrent
    self.add_torrent_ns(filename, save_dir, compact)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 801, in add_torrent_ns
    self.state.torrents.append(new_torrent)
AttributeError: 'dict' object has no attribute 'append'

```

I have tested this link but it didn't work
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=583](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=583)

Please help me understand what the problem is

---

### Post by Jerzabek39 on 2008-01-04
I had the same problem, but for me it works with the "try rm ~/.config/deluge/persistent.state"

---

