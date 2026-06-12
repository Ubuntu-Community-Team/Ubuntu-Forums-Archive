---
title: "rtorrent . induvidual speed settings"
date: 2007-09-07
forum: General Help
---

### Post by olavjunior on 2007-09-07
I just started using rtorrent, and it's fab! 

But one feature I miss, is to be able to give torrents individual speed settings, or ratio setting. 

This is very helpful since I use some closed trackers where ratio is a very good thing, and others open which occupy all of my network.

---

### Post by Harry_Sack on 2007-09-13
I used 

> # Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,stop_on_ratio=170,100M,200

for controlling ratio until today, but it doesn't seem to work in v.0.7.7...

However, if you get it to work, you can use I (SHIFT+I) to set torrents to ignore commands.
Then it will seed for ever.

---

### Post by shirilover on 2007-09-14
change schedule = ratio,60,60,stop_on_ratio=170,100M,200 
to schedule = ratio,60,60,"stop_on_ratio-170,100M,200"

---

### Post by Harry_Sack on 2007-09-14
Cheers!:smile:

---

