---
title: "first commercial DVD read attempt under 18.04 no go"
date: 2019-03-21
forum: General Help
---

### Post by JamButty on 2019-03-21
In the last few years, VLC has always been able to read commercial DVDs after
```
sudo apt-get install libdvd-pkg
sudo apt install ubuntu-restricted-extras

```
Just tried for the first time under 18.04 with 3 DVDs, all of which play in Windows and VLC is unable to play them. It briefly reads and displays the title of the films, then stops. I try opening within VLC as disc and opening individual VOB files - nothing works.

Are there new DVD kinks under 18.04?

---

### Post by TheFu on 2019-03-21
Yes. snaps.  **snap list** will show the packages installed using snaps.  The old, normal, non-snap, version of VLC is still available. Install that.
There might be some settings you can make to keep using the snap, but relax to security to allow VLC's plugins to work.  IDK.
[https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)

---

### Post by JamButty on 2019-03-21
```
sudo dpkg-reconfigure libdvd-pkg
```
was the bit I was missing. Now it works, thanks!

---

