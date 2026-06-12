---
title: "Cannont get mpd to access music collection"
date: 2007-09-11
forum: General Help
---

### Post by kinjin on 2007-09-11
I installed mpd, but I am having a problem with it. I have all my music located on an NTFS partition. I created a symbolic link in my home directory to the location on the NTFS partition and then I updated the /etc/mpd.conf file. When I try to create the mpd database I get this: sudo mpd --create-db
cannot open music_directory "/home/bob/music/" (config line 8 ): Permission denied. How can do I allow mpd to access these files?

---

### Post by martin_prince on 2007-09-13
Try to type this in a terminal:
```
cd /home/bob/music/
```
does that give you an error message or does it just come back with another prompt (meaning it was successful).  If it gives you an error message, then you have a typo somewhere or are not looking in the righ place (remember it is case sensitive).  If it doesn't give you an error, then you can browse to "music" in your home folder in nautilus, right click on it, and click on the permissions tab.  Change the permissions so that everyone can access it and try that...

Hope that helps...

---

