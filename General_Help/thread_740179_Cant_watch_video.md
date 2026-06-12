---
title: "Cant watch video"
date: 2008-03-30
forum: General Help
---

### Post by ftblplyr46 on 2008-03-30
Ive downloaded a few video's via torrents, and it wont let me view them.  I try to open them up, and it says something bout them being a text file.  They are AVI format.  I then try to download the VLC player through Synaptic and get this...

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: ttf-dejavu  but it is not installable


What do I need to do?


Edit:  I downloaded one video, and was able to view it.  The problem came from the 2nd file.  Says its a text file?

---

### Post by Michael.Godawski on 2008-03-30
try in terminal

```
sudo apt-get install vlc-nox ttf-dejavu
```

I do not want to be the dog in the manger but video files in the torrent network are somewhat fishy to me...

---

### Post by danwood76 on 2008-03-30
It depends on your torrents source.
Public trackers are usually very iffy and are to be avoided, good private trackers are normally very good.

How can you be sure the video you downloaded is actually a video and not a windoze viruz/trojan?

---

### Post by blondebeard on 2008-03-30
do a search in add/remove programs for CODEC. install the codec that has .avi in the description. if that doesnt do it you might have a corrupt file which will happen with p2p.

---

### Post by ftblplyr46 on 2008-03-30
> **danwood76 said:**
> It depends on your torrents source.
Public trackers are usually very iffy and are to be avoided, good private trackers are normally very good.

How can you be sure the video you downloaded is actually a video and not a windoze viruz/trojan?

What is a private tracker?  Ive just mainly used thepiratebay.  Havent had any problems so far with it.

---

