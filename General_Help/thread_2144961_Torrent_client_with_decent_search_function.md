---
title: "Torrent client with decent search function?"
date: 2013-05-13
forum: General Help
---

### Post by dd1linux on 2013-05-13
I'm sure this is a topic which has been covered a thousand times here, and I apologize.  However, I want a torrent program with a good webui and built in search function.  I had torrentflux, but the search function basically did not work at all.  Occasionally I would get some hits from mininova, but all the torrents showed 0 seeds.  All other search engines returned nothing.  I also installed transmission, but as far as I could tell, there was NO search function at all (maybe I just needed to install a plugin??).  Any help would be GREATLY appreciated.  Also, I am terrible at explaining my problems, so if you have any doubt about what I am asking, just ask me to clarify.  Thanks again.

Edit:  I also tried Vuze, but was never even able to bring up the webui.  Even though I installed through apt-get, I believe there was some problem with Java.

---

### Post by lisati on 2013-05-14
*Thread moved to **General Help**.*

---

### Post by slickymaster on 2013-05-14
You can try [qBitTorrent]("http://qbittorrent.sourceforge.net/"). It provides a interface complete with an in-built search engine. There’s a whole host of usual features including support for encryption, uPnP, IPv6 and RSS.
You can also remotely control qBitTorrent with the web UI.
It's in the repos or you can run the following into the Terminal:
```
sudo apt-add-repository ppa:hydr0g3n/ppa
sudo apt-get update
sudo apt-get install qbittorrent
```

---

### Post by dd1linux on 2013-05-14
slickymaster,

I installed qbittorrent, and qbittorrent-nox.  I can access the webui by going to myserverip:8080, but nothing works at all.  For example, if I click on file->add torrent file, or tools->options, nothing happens.  Furthermore, there is no search function.

---

### Post by slickymaster on 2013-05-14
> **dd1linux said:**
> slickymaster,

I installed qbittorrent, and qbittorrent-nox.  I can access the webui by going to myserverip:8080, but nothing works at all.  For example, if I click on file->add torrent file, or tools->options, nothing happens.  Furthermore, there is no search function.

Sorry if I can not provide you with any help, regarding that. But have you tried the [Bugs]("http://bugs.qbittorrent.org/") section of their site?

---

