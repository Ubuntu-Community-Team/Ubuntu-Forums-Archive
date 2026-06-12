---
title: "Wrong channelmapping in vlc"
date: 2005-10-18
forum: General Help
---

### Post by M7S on 2005-10-18
Hi.

I can't get the channelmapping right in vlc. The center channel comes out of rear left and so on. I use alsa, by the way.

I guess the problem is that vlc doesn't use the device surround51, since I get the same odd channel mapping when I test the surround sound with speaker-test -c6 as I get in vlc but I get the correct channelmapping when I use speaker-test -c6 -Dsurround51.

I have tried to run vlc with --alsadev surround51 but that results in a broken pipe and choppy suond. I've also tried to change alsadev=default to alsadev=surround51 in ~/.vlc/vlcrc but vlc reverses that to alsadev=default when vlc starts (or when it exit?) so that doesn't help either.

I hope my crappy english makes any sence... Is there any solution to my problem?


M7S

---

