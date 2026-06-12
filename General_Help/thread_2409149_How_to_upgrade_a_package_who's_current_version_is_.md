---
title: "How to upgrade a package who's current version is not in the repository?"
date: 2018-12-28
forum: General Help
---

### Post by jjhudak on 2018-12-28
I am running Ubuntu server 16.04 LTS and recently installed music player daemon (mpd) from the package repository (e.g. apt-get update, apt-get install mpd).
  The version that was installed was 19.3 (built early 2016).  The current version of mpd is 21.2 (built Nov 2018). 
Several major bug fixes have occurred over this time period and I want to install the most current version.


  Can someone please point me to a document or provide advice on how to do this (so I don’t break the existing configuration)?
  Is upgrading in this fashion generally a good idea?  
I am wondering if updated dependency files needed by the newest version of mpd might not work with the rest of the server 16.04. 
Help much appreciated
J

---

### Post by Impavidus on 2018-12-28
When a version of Ubuntu is released, the software on it is frozen. There's an exception for major bugfixes and a few selected applications, but most if stays at the version it was. That's why Ubuntu 16.04 has an older version of the software you want. The advantage is more stability.

You could upgrade the entire system to Ubuntu 18.04, which will get you mpd 20.18, but this upgrade has some risks and it may be overkill. You can also try and find a PPA for mpd on 16.04. That's probably best. Use a search engine to find one that looks reliable and well maintained, then install it. PPAs can cause issues, but if you find one made for Ubuntu 16.04 it'll probably be fine.

---

### Post by oldos2er on 2018-12-28
There's [https://github.com/MusicPlayerDaemon/MPD;](https://github.com/MusicPlayerDaemon/MPD;) it's up to you whether to trust this source or not.

---

