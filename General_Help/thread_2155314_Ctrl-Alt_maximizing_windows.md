---
title: "Ctrl-Alt maximizing windows"
date: 2013-06-17
forum: General Help
---

### Post by plkoij on 2013-06-17
Every time I press Ctrl+Alt, it maximizes the current window. This is really annoying when I'm using keyboard shortcuts to switch between workspaces. It started happening when I used xmodmap to remap some keys (number pad, num lock), but I've undone that and I can't get it to stop. Any ideas what could be causing this? I'm using Ubuntu 13.04. Thanks

---

### Post by |{urse on 2013-06-17
[FONT=Ubuntu Mono]The command to reset your keymap is

> setxkbmap -layout us

of course, change us to the appropriate regional layout if you aren't in the us[/FONT]

---

### Post by plkoij on 2013-06-17
That didn't fix it. I did disable the keyboard shortcut for toggle maximization state (all my other window keyboard shortcuts were already disabled), and now instead of maximizing, every time I press Ctrl+Alt it moves the window to the top half of the screen and toggles through various window widths.

---

### Post by |{urse on 2013-06-18
Weird! unfortunately that was my only guess on this one.. bump.

---

### Post by 3rdalbum on 2013-06-19
Check the settings in Compizconfig Settings Manager.

---

### Post by MidnightGrey on 2013-06-19
> **plkoij said:**
> It started happening when I used xmodmap to remap some keys (number pad, num lock), but I've undone that and I can't get it to stop

The question is what were your **exact** xmodmap commands, and what did you do to reverse them?

---

