---
title: "xrandr/xgamma changes lost after tty"
date: 2017-02-26
forum: General Help
---

### Post by tigerjack89 on 2017-02-26
I have a small startup scripts that run whenever I log-in into my desktop session and, among other things, it runs
```
xrandr --output LVDS1 --gamma 1:1:0.75
```
to change the gamma value.

However, those changes are lost every time I access, for some reason, one of the tty console and get back to the desktop session.

Is this supposed to be the normal behaviour? Is there any chance to make this setting persist after switching between tty/desktop sessions?

I already tried using ```
xgamma -bgamma 0.75
``` in place of the previous code, but the behaviour is exactly the same.

---

