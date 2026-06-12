---
title: "Menu/Text Rendering Issue"
date: 2014-03-12
forum: General Help
---

### Post by rackit on 2014-03-12
Running Saucy with Intel Haswell Mobile graphics. Compiz crashed and when I rebooted, text in menus and what-not is rendering odd (anti-aliasing maybe?). When I delete ~/.config/dconf/user, it all goes back to normal until Compiz crashes and it's back to wonky text. Compiz doesn't crash while the text is rendered wrong - only when it's "proper". Has anyone experienced this? Any suggestions to make it render properly without crashing compiz? I'm poking around in dconf-editor and will post if I come up with something.

[ATTACH=CONFIG]251088[/ATTACH]

---

### Post by rackit on 2014-03-12
Well, that was quick! Here's what worked:
dconf-editor
[I]/org/gnome/settings-daemon/plugins/xsettings
changed rgb order to rgba

[/I]All other rgb order options resulted in the "issue"[I].

[/I]For you cli types,  ```
gsettings set org.gnome.settings-daemon.plugins.xsettings rgba-order 'rgba' 
```

BTW, the monitor is a 46" touchscreen rotated 90° ccw. Don't know if that matters. It's calibrated so I don't want to rotate it to normal to experiment.

---

