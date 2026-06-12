---
title: "rTorrent watch_directory not working"
date: 2014-01-03
forum: General Help
---

### Post by ripster1121 on 2014-01-03
I am having trouble getting watch directories to work in rTorrent.

  I have this in my .rtorrent.rc file:

  schedule = watch_directory,5,5,"load_start=/home/rtorrent/watch/*.torrent"
schedule = untied_directory,5,5,stop_untied=

  There are 4 torrent files in /home/rtorrent/watch but none of them are showing up in rtorrent.

  [B]Versions
[/B]ruTorrent: 3.6
rTorrent: 0.9.2
libtorrent: 0.13.2

Does anyone know what could be causing these to not work?

---

### Post by andrew.46 on 2014-02-04
Hmmm... these settings are pretty much the same as mine, although I do not use ruTorrent. Only small difference, which is possibly inconsequential, is that I do not have the quotation marks:

```

schedule = watch_directory,5,5,**[COLOR="#FF0000"]"[/COLOR]**load_start=/home/rtorrent/watch/*.torrent**[COLOR="#FF0000"]"[/COLOR]**
schedule = untied_directory,5,5,stop_untied=

```

so perhaps try without these. If this makes no difference could you post your entire .rtorrent.rc file and perhaps a further hint can be seen in it...

---

