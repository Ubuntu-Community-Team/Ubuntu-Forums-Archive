---
title: "Media Keys with ncmpc?"
date: 2008-06-01
forum: General Help
---

### Post by flintmecha on 2008-06-01
I have recently started using ncmpc as my music player and I totally love it. But there is one problem. I can't figure out how to bind my laptop's media keys (Play/Pause, Back, Stop, etc etc..) to it. It is extremely annoying having to first pull up ncmpc (because the current key bindings aren't global, the terminal with ncmpc has to be the active window) and then press an awkward key combination to do some basic task when I have what should be dedicated buttons right here in front of me. 

I have already gone to System > Preferences > Keyboard Shortcuts and I have the following already set:
Play (or Play/Pause):  XF86AudioPlay
Stop playback:  XF86AudioStop
Previous track:  XF86AudioPrev
Next track:  XF86AudioNext

But it doesn't want to work with ncmpc. I have tried going to ncmpc's keybindings screen to edit them, but ncmpc doesn't even seem to recognize when I press one of those keys because I can't set them. Is there a more manual way of configuring the keys?

Thanks.

By the way, I'm using Ubuntu 8.04.

---

### Post by flintmecha on 2008-06-03
Bump?

---

### Post by El_Belgicano on 2008-06-15
You could install sonata and minimize it to tray everytime ...

---

### Post by mali2297 on 2008-06-15
I suggest that you use the small command line tool **mpc**, install it with Synaptic. If you're using Metacity, go to apps/metacity in gconf-editor to set up custom keyboard shortcuts. If you're using Compiz, use the Compiz settings configuration manager.

Suitable setup:
[indent]
"XF86AudioNext" -> "mpc next"
"XF86AudioPrev" -> "mpc prev"
"XF86AudioStop" -> "mpc stop"
"XF86AudioPlay" -> "mpc toggle"
[/indent]

This way, you can control the music player daemon without having ncmpc open.

---

