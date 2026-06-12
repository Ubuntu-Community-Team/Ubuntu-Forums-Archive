---
title: "Keyboard-mashing ran some commands.  How to find out what they were?"
date: 2021-01-27
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-01-27
While I was testing something, I was randomly keyboard-mashing to generate dummy text.  My keyboard "re-initialised" during this time (such "re-initialisations" are a known artifact of my setup) and some key(s) registered as stuck down.  I believe one of them was my Meta key.

But it took me too long to figure out this happened, and I ended up hitting several keyboard shortcuts that ran some commands.

First visible effect was that I couldn't click in Openbox's window titles.  Ok, that's just what happens when Meta key is held down, no problem.

Next, the Xfce display settings popped up.  Ok, found what shortcut triggered that, and removed it as I don't need it.

Then, Konsole opened and showed a list of mostly-local IP addresses and my hostname, in a three-column format, and showed "so" at the next shell prompt??

Then a bunch of KDE-related processes I don't have tried to run and failed.

This happened both in a Xubuntu 20.04 VM I was running at the time, and subsequently on the host OS.

Is there some way I can find out what all commands I unintentionally ran? (That is, without keyboard-mashing again :p )  I'm unsure whether I could have damaged something, especially since I didn't set the keyboard shortcuts that were activated 8-[ Thanks.

---

### Post by dragonfly41 on 2021-01-27
Does running history command show last rogue commands?

---

### Post by &amp;KyT$0P# on 2021-01-27
> **dragonfly41 said:**
> Does running history command show last rogue commands?

Sorry, I should have mentioned I tried that and it doesn't show any of the rogue commands.

---

### Post by &amp;KyT$0P# on 2021-02-03
bump

---

### Post by dragonfly41 on 2021-02-03
Next idea.
Launch Synaptic Package Manager.
Go to File > History

---

### Post by &amp;KyT$0P# on 2021-02-03
> **dragonfly41 said:**
> Next idea.
Launch Synaptic Package Manager.
Go to File > History

That only shows package transactions I intentionally did through Synaptic.  Looking more generally through [FONT=Courier New]/var/log/apt/history.log[/FONT] archives also only shows things I did intentionally.

---

### Post by &amp;KyT$0P# on 2021-08-06
> **halogen2 said:**
> Then, Konsole opened and showed a list of mostly-local IP addresses and my hostname, in a three-column format, and showed "so" at the next shell prompt??

This happened again.  Turns out this was Meta+O, and it actually happens if I press Meta + just about any letter key when a Konsole window is focused: something prints a list of hostnames and IPv6 addresses that are in my HOSTS file, arranged in columns, then pre-fills the next shell prompt with the letter s followed by the key I pressed.

What is it running and where is this "keyboard shortcut" coming from?

---

### Post by T6&amp;sfpER35% on 2021-08-07
in terminal if you press arrow up key it shows previous command typed
each time you press arrow it shows previous command

---

### Post by &amp;KyT$0P# on 2021-08-07
> **3nd said:**
> in terminal if you press arrow up key it shows previous command typed
each time you press arrow it shows previous command

Unfortunately, as noted earlier this one does not show up there.

---

