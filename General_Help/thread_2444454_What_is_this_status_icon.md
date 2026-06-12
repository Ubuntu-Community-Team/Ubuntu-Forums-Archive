---
title: "What is this status icon?"
date: 2020-05-30
forum: General Help
---

### Post by axarp on 2020-05-30
It shows up every now and then blinks a few times then disappears for a min or so..

[IMG]https://i.imgur.com/b5oToLf.jpg[/IMG]

Clicking on it just opens dropdown for nework, audio, settings, power etc..
Running Ubuntu 20.04 LTS.

---

### Post by daniewicz on 2020-05-30
Shouldn't disappear. What shell theme are you using?

---

### Post by CatKiller on 2020-05-30
That looks like a power cable to me.

---

### Post by DuckHook on 2020-05-31
Is it a warning that you have insufficient/dirty power to/from PSU? I get a lightning bolt on top right corner of RPi display when it detects insufficient/dirty power from transformer. Never seen it on a typical desktop though.

---

### Post by axarp on 2020-05-31
Sorry this is a laptop Dell XPS 15 9570 with OEM power through barrel and it working fine. This is Yaru dark theme... Upon searching yaru source code, it seems it's related to "thunderbolt-acquiring".. I am using a USB C dock.. now if you can help me further investigate if this is an issue that it's doing this periodically is normal or potential problem?


Thanks for your help.

---

### Post by daniewicz on 2020-05-31
I have a Dell XPS 13 9630 running Windows 10. For a time there were several updates issued by Dell that were USB C dock related, including a BIOS update. Is your laptop a dual boot so that you can run Dell Update?

---

### Post by DuckHook on 2020-05-31
> **axarp said:**
> …Upon searching yaru source code, it seems it's related to "thunderbolt-acquiring"…
Are you sure? My research shows the thunderbolt icons to all be variants of a lightning bolt, as one would expect. If I were to guess what your icon means, it would be something to do with system power. After all, it's a power cord. The three dots may mean power level or battery charge level. It's hard to chase down what icons mean when we don't have your HW or your system theme. Do your logs tell you anything?

---

