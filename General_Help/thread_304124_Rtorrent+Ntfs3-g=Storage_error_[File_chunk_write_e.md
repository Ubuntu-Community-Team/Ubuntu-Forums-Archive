---
title: "Rtorrent+Ntfs3-g=Storage error: [File chunk write error: No such device]"
date: 2006-11-21
forum: General Help
---

### Post by Citro on 2006-11-21
I use Ntfs-3g to write/read on my disks but if I use rtorrent to download something it gives me the error in topic.

Looked here [http://libtorrent.rakshasa.no/ticket/226](http://libtorrent.rakshasa.no/ticket/226) but I dont use Fuse but it looks like  the same error.


The weirdest thing is that I can use Utorrent via Wine and write to NTFS-disks.:confused:

---

### Post by kragen on 2006-11-24
ntfs-3g uses FUSE (I think). Thats probably why you are having the same problem (me too)

Looks like i'm either gonna have to save my torrents to an ext3 partition, or use another bittorrent client :(

---

