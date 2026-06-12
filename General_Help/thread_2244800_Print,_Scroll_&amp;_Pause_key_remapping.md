---
title: "Print, Scroll &amp; Pause key remapping"
date: 2014-09-18
forum: General Help
---

### Post by CliveMcCarthy on 2014-09-18
I want to map **Print Screen, Scroll Lock, **&** Pause** keys to **Cut, Copy **&** Paste**, that is to Control_x, Control_c & Control_v

I've read a few posts on how to approach the subject and editing **/etc/console-setup/remap.inc** seems like the way to go.
I have run **xev** to detect the keycodes and looked at the code in **dumpkeys** -- they don't agree with **xev** so I put BOTH in the remap:

I added these lines:
```
[INDENT][B]keycode    70 Control_c
keycode  107 Control_c
keycode    78 Control_x
keycode  119 Control_v
keycode  127 Control_v[/B]
[/INDENT]
 
```to **remap.inc** and then I ran **sudo dpkg-reconfigure console-setup** and rebooted my system.

It doesn't work!
Hmm. Any ideas? This should be super easy...

Later: I think I need to get into xkb?

The relationship between Gnome (I'm not a Unity user) and Xorg and Linux is evidently confusing me. 

I just got xmodmap to accept:** xmodmap -e "keycode = 127 Control_L v "** but I gather that Gnome, which is layered on X, handles it's own key mappings. So my key mapping could work in a pure X-interface but not for Gnome? So where does Gnome hide its mapping? Too many cooks spoil the broth :frown:

---

