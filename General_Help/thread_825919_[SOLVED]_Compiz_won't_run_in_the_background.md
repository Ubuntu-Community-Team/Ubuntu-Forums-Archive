---
title: "[SOLVED] Compiz won't run in the background"
date: 2008-06-11
forum: General Help
---

### Post by ByKeLaO on 2008-06-11
Hi guys!
Compiz doesn't play nicely with Steam on my PC, so I decided to write a bash script that disables compiz, runs steam, and then re-enables it. I then want to run avant-window-navigator after compiz has been re-launched. However, compiz won't run in the background, and so the last part of my script never gets run!
Here's the code:

```
kill `pidof avant-window-navigator`
metacity --replace &
export WINEPREFIX="/home/james/.WineBottles/Steam" && wine "C:\Program Files\Steam\Steam.exe"
compiz --replace &
avant-window-navigator
```

It gets to compiz --replace & and then stops because compiz refuses to start in the background.
Any ideas on how to fix this?

---

### Post by ByKeLaO on 2008-06-11
I'm not sure I understand why... but logging out and back in again seems to have done the trick...
-sigh- sorry for wasting your time, people...

---

