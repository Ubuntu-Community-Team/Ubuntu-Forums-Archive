---
title: "rTorrent / resuming torrents?"
date: 2007-12-07
forum: General Help
---

### Post by ~LoKe on 2007-12-07
I've decided to ditch my utorrent/wine combo and go with rTorrent instead.  I'm pleased with it thus far, but I have one concern..

When I restart x, reboot, etc, and re-open rTorrent, my existing torrents no longer appear.  My questions are simple:

1.  Is there any way to automatically load the torrents that were downloading?
2.  If I manually load the torrent again, will it continue where it left off?

---

### Post by ~LoKe on 2007-12-07
Any ideas?

---

### Post by konsole on 2007-12-08
1. you need this option in your .rtorrent.rc  [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide#Sessiondirectory](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide#Sessiondirectory)

2. rtorrent will hash check the downloaded file pieces and continue from where it left off.

---

