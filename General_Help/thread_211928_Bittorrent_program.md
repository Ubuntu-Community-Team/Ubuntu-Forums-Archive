---
title: "Bittorrent program?"
date: 2006-07-09
forum: General Help
---

### Post by boom2k1 on 2006-07-09
What is the best bittorrent program in Ubuntu?

---

### Post by yosoyviejo on 2006-07-09
> **boom2k1 said:**
> What is the best bittorrent program in Ubuntu?

Even if it's ultra-slow (but that's because of Java), Azureus. Other clients just don't give me all the features I need. A client for Windows which I would really love to see ported to gnu/linux is BitComet.

---

### Post by boom2k1 on 2006-07-09
Is there a program that resembles bitcomet??

The bittorrent doesn't really work!

---

### Post by krazyd on 2006-07-09
utorrent is a good torrent client which works well with wine.

---

### Post by boom2k1 on 2006-07-09
Does anybody have this kind of problem before with Bittorrent?

BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:58) 
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 476, in onInvoke
    apply(event.func, event.args, event.kwargs)
  File "/usr/bin/btdownloadgui", line 2019, in onChooseFile
    if d2 == default:
UnicodeDecodeError: 'ascii' codec can't decode byte 0xa5 in position 0: ordinal not in range(128)


How do you fix it? Thanks!

---

### Post by gingermark on 2006-07-09
[rubbish]

---

### Post by FredB on 2006-07-09
> **krazyd said:**
> utorrent is a good torrent client which works well with wine.

utorrent *seems* to be not very reliable about user respect. And with azureus, you can use Safepeer and be free of any spying.

And why using a Win32 programs if there is good linux based one ?!

---

### Post by FredB on 2006-07-09
> **boom2k1 said:**
> Does anybody have this kind of problem before with Bittorrent?

BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:58) 
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 476, in onInvoke
    apply(event.func, event.args, event.kwargs)
  File "/usr/bin/btdownloadgui", line 2019, in onChooseFile
    if d2 == default:
UnicodeDecodeError: 'ascii' codec can't decode byte 0xa5 in position 0: ordinal not in range(128)


How do you fix it? Thanks!

Erh... Did you install it with Synaptic / Adept ?

---

### Post by pravuil on 2006-07-09
Kudos! Thanks Fredb. I was wondering about an alternative to linblock and you answered it for me.

---

### Post by cleentrax on 2006-07-09
I really like Bittornado. It has low overhead, unlike Azureus, and has the features I need (that are not in the basic Bittorrent client).

---

