---
title: "how to bind albert to CTRL+SPACE in 17.10?"
date: 2017-12-27
forum: General Help
---

### Post by sa3 on 2017-12-27
Something in 17.10 is preventing me from binding CTRL+SPACE to be the launcher key for albert. When I'm in certain windows it will work (e.g. firefox), but in any "os" windows, e.g. terminal, file browser, settings window, etc., CTRL+SPACE does not bring up albert. When I'm in the file browser, CTRL+SPACE seems to do something with the currently selected file (can't figure out what). I've been looking around in gnome-tweak-tool for a way to disable these existing hotkeys, but I can't seem to find where they are defined. This was working fine in 16.04. Please advise

Thanks!

---

### Post by DuckHook on 2017-12-28
*Thread moved to **General Help** as the more appropriate forum.*

---

### Post by Holger_Gehrke on 2017-12-28
ctrl-anything is a bad idea for a system wide hotkey, because this kind of key combination is used by a lot of programs for application hot keys. ctrl-space is mark/unmark the current file in most file managers and inserts a non-breaking space in most - if not all - word processors. By your description I think albert seems to put itself at the very end of the list of programs processing keyboard events, so you should select some key you know nothing else uses - ctrl-shift-space seems a good candidate to me and works while in a terminal or in the file manager.

Holger

---

### Post by raleigh3 on 2017-12-28
Ctrl Alt "Any letter" is good also as a hotkey.

---

