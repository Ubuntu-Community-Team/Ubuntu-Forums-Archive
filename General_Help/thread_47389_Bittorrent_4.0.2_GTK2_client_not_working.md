---
title: "Bittorrent 4.0.2 GTK2 client not working"
date: 2005-07-08
forum: General Help
---

### Post by kaput on 2005-07-08
I recently tested FC4 for a few weeks and fell in love with Bittorrent's new GTK2 client (built on btdownloadgui.py). The "official" .deb ([here]("http://www.bittorrent.com/dl/bittorrent-4.0.2.linux_i686-2_all.deb")) is seriously busted, but installable. However, when I run the script, I get the following error:

```
$ ./btdownloadgui.py
Traceback (most recent call last):
  File "./btdownloadgui.py", line 33, in ?
    from BitTorrent import configfile
ImportError: cannot import name configfile

```
Anybody have it working? I'd love to be able to use it within Ubuntu.

---

