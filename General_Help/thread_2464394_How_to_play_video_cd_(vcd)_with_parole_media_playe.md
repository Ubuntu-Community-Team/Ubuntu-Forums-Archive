---
title: "How to play video cd (vcd) with parole media player?"
date: 2021-07-01
forum: General Help
---

### Post by hiepvs on 2021-07-01
the parole media player can't play video cd (vcd) disk, what dependencies are missed? Thanks

---

### Post by monkeybrain20122 on 2021-07-01
> **hiepvs said:**
> the parole media player can't play video cd (vcd) disk, what dependencies are missed? Thanks

libdvdcss2
[https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)

---

### Post by Holger_Gehrke on 2021-07-01
@monkeybrain20122: Nope, VCD doesn't use the Content Scrambling System. It's a simple MPEG1 stream in a mode 2 track (so no error correction and no copy protection).

@hiepvs: If you've got all the plugins for the gstreamer framework installed (gstreamer1.0-plugins-{base,good,bad,ugly}) and it still doesn't work with parole, then you'll probably have to try another player. VLC supposedly can play VCD, but I haven't had any VCDs for years and therefore can't verify that information

Holger

---

