---
title: "[SOLVED] xorg problems (?): touchpad slow, no greek keyboard"
date: 2007-09-30
forum: General Help
---

### Post by alexmoon on 2007-09-30
I used [these]("http://ubuntuforums.org/showthread.php?t=31076") instructions to enable me to switch between dvorak and greek keyboard layouts by pressing both 'shift keys'. It worked really well for ages. Recently, it stopped working - I would press the shift keys, and nothing happened, it just stayed in Dvorak. When I go to system -> preferences -> keyboard -> layouts and move the greek keyboard up, it still stays in Dvorak.

This might be related to a mistake I made - after changing xorg.conf, a window appeared on login and asked if I wanted to use the x server or gnome settings. I chose "x server", and "never ask me again". I'm sure there must be a way to reverse this and use gnome settings, but I don't know what it is.

Any advice would be greatly appreciated. I get the feeling that I've made a really silly mistake somewhere along the line, I just don't know what it is.

EDIT: Solved - I had to change the part of xorg.conf that read "dvorak,greece" to "dvorak,gr". Not sure what happened here - if the code was just changed from "greece" to "gr" or something? Anyway, it's fixed now.

---

