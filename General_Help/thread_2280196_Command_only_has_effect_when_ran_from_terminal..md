---
title: "Command only has effect when ran from terminal."
date: 2015-05-28
forum: General Help
---

### Post by Garchomps on 2015-05-28
[COLOR=#111111][FONT=Ubuntu]I'm on Xubuntu 15.04. I'm trying to run command: [/FONT][/COLOR]xss-lock -- xscreensaver-command -lock &[COLOR=#111111][FONT=Ubuntu] so that my screen will lock after being suspended in Xubuntu using xscreensaver. For some reason, without running this command, Xubuntu will only lock the screen after suspension via the suspend button, but not by shutting the laptop lid like it's configured to. In the Arch wiki where I got this command (it applies equally to Ubuntu since they'd be both using systemd, xfce, and X.org in this scenario, I think) it says to run this command from the X session autostart script. I've tried running this command from xinitrc, rc.local, xfce4's xinitrc, and on session autostart. It will ONLY take effect if I run it from inside a terminal after everything else has started. Why is this? How can I get it to run automatically when X.org starts? Thanks to anyone who would help! :D[/FONT][/COLOR]

---

### Post by Toz on 2015-05-31
It won't work in xinitrc, rc.local or xfce4's xinitrc because the command requires a valid X display and one doesn't exist at those points during the login process. However, it should work in the session startup (Settings Manager >> Session and startup >> Application autostart). When you have it in the application autostart, is it running after you log in?
```
pgrep -a xss-lock
```

If so, try going to xscreensaver's settings and on the Advanced tab, uncheck the "Fade to black when unblanking" option.

---

