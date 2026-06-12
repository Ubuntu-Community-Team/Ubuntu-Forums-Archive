---
title: "please help with ktorrent and ted"
date: 2006-12-14
forum: General Help
---

### Post by CyberCod on 2006-12-14
I am setting up an ubuntu machine for my TV addicted mother-in-law.

I need to make it as easy as possible.

I've got  TED (torrent episode downloader) and it is working fine.  As well as ktorrent which is also working fine.  

The problem is that TED does not automatically start up downloads in ktorrent, though it does have an option to start them with the default bit-torrent client.

I have tried changing the nautilus default to "/usr/lib/ktorrent" (i think thats what it was) and now it will open up properly from a double click... but not from TED.

Any ideas here?

Thanx in advance.

---

### Post by stoeptegel on 2006-12-18
KTorrent has a scanfolder plugin, maybe that can help you.
Just configure KTorrent to observe a folder, mark the option to load torrents silently, and give the downloads a default storage location.

Then if you would configure TED to save the torrent files in the same path as KTorrent is monitoring you should be gold.

Note that KTorrent has a RSS plugin on it's own now. Dunno, you might want to use that instead.

---

