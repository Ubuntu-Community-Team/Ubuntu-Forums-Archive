---
title: "Old automake?"
date: 2005-04-06
forum: General Help
---

### Post by WMCoolmon on 2005-04-06
I tried to build a multiplatform project I work on, [fs2_open](http://en.wikipedia.org/wiki/Freespace), but got some errors with the autogen file...I asked the lead Linux guy about it, turns out that I need automake 1.7+ and the one in the repository is only 1.4.

I'm relatively new to the linux scene (If you haven't guessed already ;) ) so I dislike compiling from source if I can help it, since rpm/apt repositories make things much more organized and easier to install/upgrade packages without having to follow the progress of each individual one.

So I'm curious why only version 1.4 of automake is in the repository, when apparently they're up to 1.9? (I have added the additional repositories as specified in the unofficial getting-started guide, although a couple didn't work for me.)

---

### Post by WMCoolmon on 2005-04-06
Oops, I just realized my problem...apparently apt-get dist-upgrade doesn't do automake as they're in separate packages.

Mods, feel free to close this thread (Or put solved).

---

