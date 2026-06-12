---
title: "Upgraded to Hirsute Hippo and application windows are garbled"
date: 2021-06-06
forum: General Help
---

### Post by backinthesaddle on 2021-06-06
Upgraded to Hirsuite Hippo today, and the screens of applications like Chrome, Firefox, Spotify, Virtualbox, and Anaconda are completely garbled with blocks of white, black, and green. But Gnome specific things like my folder windows, terminal, and my desktop environment show up just fine. 

Booting into recovery mode 5.11.0-18-generic lets me use the applications though. Going back to 5.8.0-55-generic loads everything correctly. So, there's something that the 5.11.0-18 kernel doesn't agree with.

Does anybody know what might be a reason for this? Tried Googling it up, but I can't seem to find anything.

---

### Post by monkeybrain20122 on 2021-06-06
Maybe because HH uses Wayland as default? I guess there maybe an option to log into X session in gdm? (the login screen)

---

### Post by backinthesaddle on 2021-06-08
Sorry, forgot to follow-up, but yes, this was the issue. I disabled Wayland in /etc/gdm3/custom.conf, and everything works fine. Thanks!

---

