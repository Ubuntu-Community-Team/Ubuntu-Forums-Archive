---
title: "rtGUI can't connect to rTorrent using Apache for SCGI"
date: 2013-01-27
forum: General Help
---

### Post by vockleya on 2013-01-27
I'm trying to set up a web interface for rtorrent using rtgui. I have followed all the instructions I could find on setting it up, and nothing seems to work. I have rtorrent installed and working, and I have installed rtgui from the repos and can access it through a browser. The issue is that rtgui can't connect to rtorrent. I just get a message that says "Cannot connect to rtorrent :( Please, ensure that rtorrent is running."

Rtorrent has scgi and xmlrpc configured and running, and apache has the SCGIMount directive set up, so everything should be set up correctly.

I have figured out that the scripts are most likely failing somewhere in the get_global_stats() or get_global_rates() functions called from index.php, but I have no idea what this means or how to fix it.

---

