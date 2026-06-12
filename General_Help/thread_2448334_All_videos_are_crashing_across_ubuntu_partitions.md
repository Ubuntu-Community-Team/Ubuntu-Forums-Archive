---
title: "All videos are crashing across ubuntu partitions"
date: 2020-08-06
forum: General Help
---

### Post by spencer2 on 2020-08-06
My new Ubuntu Studio 20 is not playing any videos from files. Whether its VLC or Parole, they all crash at the 5 second mark.

I can watch online videos such as youtube, but anything from a file on my laptop stops playing. The screen goes black but the program itself does not close: the video just stops.

I'd greatly appreciate some help with this please. I've been trying to figure this out for a few days now & still no luck. Pretty please with cherries on top: I'd really like to solve this.

---

### Post by CelticWarrior on 2020-08-06
Please post the hardware specifications, namely the graphics.

---

### Post by SeijiSensei on 2020-08-06
Any better with mpv?  If so, install SMPlayer for a nice GUI front-end.

```
sudo apt install mpv smplayer
```

---

### Post by HermanAB on 2020-08-06
Quite a head scratcher.

Some ideas for investigation:
a. Is there enough /tmp space.
b. Is there Swap space.
c. Run top in a terminal and watch it.
d. If the screens go black, run OpenSSH and log in from another machine to observe what is happening.

---

