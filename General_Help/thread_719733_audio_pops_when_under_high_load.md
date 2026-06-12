---
title: "audio pops when under high load"
date: 2008-03-09
forum: General Help
---

### Post by PetePete on 2008-03-09
seems under high load audio pops.

heres the setup..
Amarok, + kubuntu 7.04 , using ALSA

laptop with 2ghz + 1gb RAM

i've got a fair few apps open at the moment, but nothing too much (firefox, eclipse, MS word, ktorrent)

whenever I do something , even browsing and loading webpages the audio starts to pop.

anything I can tweak to avoid this?

---

### Post by kuja on 2008-03-10
I would try going to System Settings -> Sound system and check the "Run with highest possible real time priority" checkbox, and increasing the sound buffer to something larger (or as large as possible, if you want it to be)

---

