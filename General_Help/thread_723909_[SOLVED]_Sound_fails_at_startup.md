---
title: "[SOLVED] Sound fails at startup"
date: 2008-03-14
forum: General Help
---

### Post by fiftyMIPsparc on 2008-03-14
I have Gutsy on an IBM T43. Recently I tried to install iTunes with WINE and it failed in a big way. Now my sound breaks at startup (I hear about half of the startup sound, then it stops and I lose all sound). I tried to uninstall iTunes through WINE to no avail. I've also tried to uninstall WINE and reinstall ALSA but that doesn't seem to be working either. Has anyone experienced this?

---

### Post by kesman on 2008-03-14
Do you get any error messages? Maybe some channel is just muted in alsamixer? In terminal, run alsamixer and hit TAB to set all channels visible. Then browse trough all of them and if there's M below the channel bar, then it's muted. Hit M to unmute the channel, ESC to exit.

---

### Post by fiftyMIPsparc on 2008-03-14
This morning when I started up my computer the problem was mysteriously fixed :confused: ... and this was after I've already restarted several times. However, I didn't think to check for muted channels, thank you for suggesting it.

:popcorn:

---

