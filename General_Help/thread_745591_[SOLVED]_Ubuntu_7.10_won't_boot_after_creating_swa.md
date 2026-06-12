---
title: "[SOLVED] Ubuntu 7.10 won't boot after creating swap file"
date: 2008-04-04
forum: General Help
---

### Post by Comrade Mike on 2008-04-04
I created a swap file for Ubuntu 7.10 yesterday using the instructions in the [swap partition FAQ]("https://help.ubuntu.com/community/SwapFaq") on the Ubuntu wiki, but now Ubuntu won't boot up. The usplash screen gets to the bit where it says it's activating the swap space or somesuch, pauses for a few seconds and then changes to a blank screen with a blinking underscore and then doesn't appear to do anything else. I figure I've probably done something wrong when creating the swap file and now plan on using my Live CD to disable the swap file. Is it possible to do this and does anyone know how? Or is there some other solution to disabling or fixing the swap file?

---

### Post by TheGoddamnBatman on 2008-04-04
What are you, stupid? Are you retarded or something? I'm The Godd&#1072;mn Batman!

---

### Post by Comrade Mike on 2008-04-05
Nevermind, I've managed to fix it now by running fsck in recovery mode.

---

