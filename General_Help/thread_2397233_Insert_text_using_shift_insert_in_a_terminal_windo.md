---
title: "Insert text using shift insert in a terminal window"
date: 2018-07-26
forum: General Help
---

### Post by raleigh3 on 2018-07-26
Using Ubuntu Mate 18.04

In most cases, shift insert works when you want to insert copied text.

  But in a terminal, it uses shift ctrl v.
  
Any way to change that behavior to shift insert?

---

### Post by TheFu on 2018-07-27
There are 20+ different terminals. Each has different default actions.  If the preferences in the terminal you use aren't doing what you want, then you can make keyboard actions whatever you need using an window-manager override.  How you do that depends on the window manager used.  I have lots of xdotool customizations running for openbox (the WM I use).

Alternative - For getting text from 1 place to another, I prefer using the X/Windows X-buffer which is a "select" + "paste" method.  No keyboard.   The "select" is just the act of highlighting **any** text on any screen, anywhere - local or remote. The "paste" is the middle mouse button.  It is much faster than copy/paste methods.  Some addon "clipboard managers" screw up the X-buffer, so I've had to remove them and I use a real xterm for my terminal program to avoid other nice things that I don't like.

---

