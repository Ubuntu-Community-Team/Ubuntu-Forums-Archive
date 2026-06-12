---
title: "[SOLVED] Desktop idle lock with password?"
date: 2007-08-04
forum: General Help
---

### Post by Hallvor on 2007-08-04
My computer is on 24/7, and many times my six year old son often comes to my computer without my knowledge to play Planet Penguin Racer. Nothing wrong with him playing that game, but he tends to close applications, make new icons on my desktop and delete others, plus opening twenty new windows and applications.

Now, is it possible to lock the desktop down after me being idle, say 10 minutes, so that the computer prompts for a password to open the desktop for use? That way, my son will have to ask me before he uses the computer, and then I can start the game for him without him doing a lot of other stuff. It would save me a bit of work.

---

### Post by aysiu on 2007-08-04
Assuming your screensaver / power settings blank the screen after ten minutes, you can ```
gconf-editor
``` and go to Apps > gnome-power-manager > lock_use_screensaver_settings

---

### Post by Hallvor on 2007-08-05
Thanks. Just what I needed. Works perfectly.

---

