---
title: "GNOME BitTorrent does not work"
date: 2005-10-25
forum: General Help
---

### Post by matthias_k on 2005-10-25
Hi,

the BT client in GNOME does not work for me. I have tried tons of torrents now, but I always get tracker timeouts from the app. It can't really be my network settings because I didn't change anything about my router settings since I installed Breezy. Ports 6881-6889 are open, I still can't connect to any tracker, seed or peer.

Any ideas?

---

### Post by Iandefor on 2005-10-25
I've had much the same trouble. I find Bittornado works well, although you do have to compile it from source to get it working under linux (to the best of my knowledge). Here's a link: [Bittornado]("http://www.bittornado.com/").

---

### Post by matthias_k on 2005-10-25
I just installed Azureus now, it works just fine (except that it fails redrawing its window properly, but at least I can download).

---

### Post by shadow on 2005-10-25
[QUOTE=Iandefor]I've had much the same trouble. I find Bittornado works well, although you do have to compile it from source to get it working under linux (to the best of my knowledge). Here's a link: [Bittornado]("http://www.bittornado.com/").[/QUOTE]

Nope, apt-get'd "bittornado" yesterday and having no problems.

It's probably handy having this in your **~/.bash_aliases** too.

```

alias btlaunch='btlaunchmanycurses.bittornado /media/files/incoming/torrents/ --minport 40000 --maxport 40009 --max_upload_rate 25 --max_uploads 4 --saveas /media/files/incoming/'

```

---

### Post by matthias_k on 2005-10-26
So, shall I file a bug? Obviously 'gnome-btdownload' does not work.

---

### Post by frenkel on 2005-10-26
[QUOTE=matthias_k]So, shall I file a bug? Obviously 'gnome-btdownload' does not work.[/QUOTE]
No, enough ppl have it working correctly (including me). Maybe it's just something specific to that tracker/torrent? Have you tried anything from other trackers? (I.E. some much used trackers seems to timeout most of the time).
Try to download the ubuntu install cd from their tracker, to test it, that should work.

---

### Post by matthias_k on 2005-10-26
No, it's not the tracker and it's not the torrent. I have tried several torrents which worked in Azureus. None of them work with gnome-btdownload.

---

### Post by frenkel on 2005-10-26
[QUOTE=matthias_k]No, it's not the tracker and it's not the torrent. I have tried several torrents which worked in Azureus. None of them work with gnome-btdownload.[/QUOTE]
Azureus uses DHT when the tracker is down, so you _can_ download it. Make sure it's not using DHT when it works in Azureus, I really think this has nothing to do with gnome-btdownload...

---

