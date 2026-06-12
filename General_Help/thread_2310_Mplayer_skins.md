---
title: "Mplayer skins"
date: 2004-10-27
forum: General Help
---

### Post by jayclark on 2004-10-27
How do I install skins for mplayer?

Jay

---

### Post by sfw5000 on 2004-10-27
The first post in this thread has detailed instructions:

[http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)

You basically just down load them from the mplayer website and then un tar it and copy the files into the mplayer Skin directory

//this shows how to set up the first skin
$ tar -xjf Blue-1.4.tar.bz2
$ sudo mkdir -p /usr/local/share/mplayer/Skin/default
$ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/

Skins: [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

---

