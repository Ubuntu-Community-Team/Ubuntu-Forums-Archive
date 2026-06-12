---
title: "Firefox crashes on myspace - possibly flash/soundcard drivers"
date: 2007-02-18
forum: General Help
---

### Post by jamespi on 2007-02-18
hi, when i browse around on myspace, firefox starts locking up, then eventually crashes. here is the terminal output.

```
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files

```
---this was repeated a million times--- 

then:
```

ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
Segmentation fault (core dumped)

```

i assume it's to do with flash and sound (which doesnt even work on my system even after i followed the thread about it)

i think maybe my sound card drivers arent working properly.

anyone have any ideas

---

### Post by tgalati4 on 2007-02-19
Myspace frequently crashes Firefox on Ubuntu for me and also Safari on the mac.  

Many Myspace pages have embedded sound and flash files that start playing immediately when the page is loaded.  Depending on how long your browse session, I believe the cache files become corrupt or a memory leak in the Java or flash player that brings Firefox down.

You could blacklist the sound modules that are not working and perhaps you will get a longer browse session.  I have found some pages to be consistently pathological--they consistently crash the browser.

Other times, it's random.  One certainty--the longer you browse, the greater your chance of crashing the browser.  

You can turn on the Javascript Console and watch the errors pile up and maybe find a trend that points to crashing the browser.

To me, a priority is to get the sound fixed, because so much of Ubuntu is tied into the sound system.

Good Luck,

Terry

---

