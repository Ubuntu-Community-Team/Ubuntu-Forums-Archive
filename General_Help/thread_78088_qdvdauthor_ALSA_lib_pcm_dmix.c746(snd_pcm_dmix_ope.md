---
title: "qdvdauthor ALSA lib pcm_dmix.c:746:(snd_pcm_dmix_open) 
qdvdauthor problem"
date: 2005-10-17
forum: General Help
---

### Post by flamarro on 2005-10-17
I want to make a dvd movie and this error shows every time....
i really dont know what to do more.
After this line
```
arecord -f dat -twav -d 1 /dev/stdout | mp2enc -r 48000 -o "/home/xxxxx/Main Menu VMGM/menu.mp2"

```
results in

```
ALSA lib pcm_dmix.c:746: (snd_pcm_dmix_open) The dmix plugin supports only playback stream

```

can't create a empty mp2 and it can't make the movie in the end, but once it has worked, but i don't know why.

--------------------------------------------------------------------------

Ok, now i've altered my settings with sound and i can manage to use arecord.
the problem now is with mplex. can't make the menu.mpg file, can't join the m2v with the mp2 file and in the end dont work. Does anybody had this problem?

---

### Post by flamarro on 2005-10-19
anyone???

---

### Post by mordarageek on 2005-12-21
I am having the same issue.  Did you ever find a solution?

---

