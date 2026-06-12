---
title: "Miro very slow"
date: 2007-08-14
forum: General Help
---

### Post by olejorgen on 2007-08-14
I installed the latest versionof miro toda. (Miro 0.9.8) It is *very* slow. 

When I ran it from from the terminal I got lots of output similar to this:
```
//podcast.happytreefriends.com/htf.jpg too slow (0.835 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa6c5a4> on HTTPClient: http://podcast.happytreefriends.com/htf.jpg too slow (0.801 secs)
TIMING   WARNING: Calling <function <lambda> at 0xb7eb17c> on HTTPClient: http://podcast.happytreefriends.com/htf.jpg too slow (1.913 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa104534> on HTTPClient: http://podcast.happytreefriends.com/htf.jpg too slow (0.770 secs)

```
(This was when browsing the happy tree friends channel and downloading 3 videos)

Playing videos also maxes out my cpu. (Xorg and miro about 50/50) EDIT: (Not all videos) (I'm using gstreamer, not xine)

I don't think this is normal (?)

My system:
CPU: AMD XP 2500
RAM: 1 GB
GPU: NVIDIA something (> TI4800)

---

### Post by apakatt on 2007-08-14
I have the same problem. Miro is very slow indeed, to slow to make it useful although i really love the interface and design.
It often uses a lot (to much) CPU. It uses 100% of my CPU, even when I'm not playing videos.

Hope it's a problem that can be solved in the future! :(

---

### Post by olejorgen on 2007-08-14
Yeha, and after a while, it used 500MB ram. Hope they can improve :)

---

### Post by Zyphrexi on 2007-11-20
I think they are at version 1 now, but version 0.9.8.1 shows up in the repos.

---

### Post by atoc on 2007-11-23
> **Zyphrexi said:**
> I think they are at version 1 now, but version 0.9.8.1 shows up in the repos.
Adding
```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```
to your sources.list will get you Miro 1.0

---

### Post by apakatt on 2007-12-02
Still super-slow I'm afraid... :( 
I would really love this app if it didn't tried to kill my CPU.

---

### Post by vanwarantion on 2007-12-06
I am using miro to download torrent files using rss feeds. Miro is very cool about that but when i run it, load average comes at 6 to 7 and increasing..

is there another app uses rss feeds to download torrents?

---

### Post by apakatt on 2007-12-06
> **vanwarantion said:**
> I am using miro to download torrent files using rss feeds. Miro is very cool about that but when i run it, load average comes at 6 to 7 and increasing..

is there another app uses rss feeds to download torrents?


Ktorrent.

---

