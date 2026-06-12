---
title: "mpd and replaygain"
date: 2006-10-06
forum: General Help
---

### Post by daedalusman on 2006-10-06
So I use mpd and gmpc to play my music and I where both are going and have no intentions of switching. In the config file I have for mpd there is an option for mpd to use replaygain. My question, how does mpd implement replaygain? Do I have to re-gain my files before mpd can take advantage of replaygain? Will it re-gain mp3, ogg, and flac? Can anyone provide me with some information on this topic? Thanks for the help and yes I know that was more than just a "question".

---

### Post by qball on 2006-11-06
Make sure you have the latest mpd (0.12.1), and have replaygain enabled in the config, that should be sufficient.

Qball

---

### Post by vanadium on 2008-03-14
See [http://www.hydrogenaudio.org/forums/lofiversion/index.php/t42005.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t42005.html)

Apparently, mpd does not read replaygain tags that are written in APEv2, as mp3gain does.

---

