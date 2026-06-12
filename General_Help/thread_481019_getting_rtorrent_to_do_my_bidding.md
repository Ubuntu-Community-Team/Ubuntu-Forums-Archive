---
title: "getting rtorrent to do my bidding"
date: 2007-06-22
forum: General Help
---

### Post by underdog5004 on 2007-06-22
I'm running rtorrent 0.7.4 with libtorrent 0.11.4 on an edgy headless server. Right now, I've got rtorrent saving everything to /media/hda3, but I've run out of room. I've got another hd of equal size that I've got in there (/media/hdc1). What I want is to have rtorrent seed from /media/hda3 and seed/leech from /media/hdc1. Any ideas?

EDIT:: Never mind, I figured it out. I transferred all my files (directories, actually) onto /media/hdc1 and put symlinks to those files on /media/hda3.

---

