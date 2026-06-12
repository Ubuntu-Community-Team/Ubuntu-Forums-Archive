---
title: "MPlayer: sound, no video in Firefox"
date: 2006-07-29
forum: General Help
---

### Post by canadianwriterman on 2006-07-29
MPlayer opens a video in Firefox, but plays only the sound. Any suggestions about how to get the video portion to play as well? Thanks, all.

---

### Post by TheRingmaster on 2006-07-29
I have the exact same problem (and post). try right clicking on the blank video and choose configure. from there make sure that everything is checked properly especially the one that says "play media directly from site". that should help to play the video. I wish there was another player we could use.

---

### Post by canadianwriterman on 2006-07-30
Found a solution. It may be that, when I installed the codecs through Automatix, the w32codecs were not installed or not installed properly. So, I added:
```

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

to my sources and then used Synaptic to download:
```

w32codecs
```

Worked like a charm after that.

---

### Post by geovino on 2006-08-10
I tried adding that address to my source.list but it seems that Synaptic can't pull in anything today. Are networks down?

---

