---
title: "Can videos play played in fullscreen by default."
date: 2015-03-31
forum: General Help
---

### Post by CaptainMark on 2015-03-31
Pretty much the question is in the title, from the file manager can I have video files play in fullscreen automatically. I'm using Nemo for a file manager and Totem as my default movie player (I am not changing from Nemo but I have no real persuasion towards Totem if it helps)

Regards
Mark

---

### Post by Holger_Gehrke on 2015-03-31
I don't know nemo, but I think you could either edit the desktop file for totem ('/usr/share/applications/totem.desktop') and change the 'exec'-line to include the option '--fullscreen' or make a copy of the desktop file under another name in '~/.local/share/applications', edit that and make this the default video player.

---

### Post by SeijiSensei on 2015-03-31
SMPlayer (in the repositories) has a setting for "Start Videos in fullscreen" under Options > Preferences > General > Video.

---

### Post by CaptainMark on 2015-04-01
Thanks for the idea, I created a seperate launcher in ~/.local/share/applications/ and called it Totem Fullscreen and set that as the default program for videos.

---

