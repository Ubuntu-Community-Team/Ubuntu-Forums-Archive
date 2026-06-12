---
title: "How to find out which program catches keypress?"
date: 2006-12-16
forum: General Help
---

### Post by Epskampie on 2006-12-16
Hi,

I recently aquired an ati remote to use on my ubuntu edgy box. It all works pretty well, but there is one thing bothering me.

I use xmodmap to bind some of the buttons on the remote to keys, like the enter key. There is one key however, that now causes ubuntu, or rather gnome, to lock the screen. 
I used xev to capture the **keycode** of the button, which is **146**. If I change the button with xmodmap to for example q, it does work, so I do get a q, but the lock screen action still occurs.

This doesn't happen on a flatmate's pc which uses KDE, so I figured a GNOME program must cause this behaviour. 
I allready checked, and it isn't the standard shortcuts, since the 'lock screen' action is set to no shortcut in the gnome configuration.
[B]
Main question:[/B]
Is there a program or some other way to find out which programs catch the keycode 146, and therefore may cause the shutdown action?

Thanks in advance,

Simon.

P.S. i used [this HOWTO]("http://www.ubuntuforums.com/showthread.php?t=95146&highlight=remote+wonder")

---

### Post by Epskampie on 2006-12-17
anybody?

---

### Post by Epskampie on 2007-06-09
Found it:

In KDE:
Some buttons are mapped to default actions in KDE, like mute (very ugly mute screen) and log out.

If you'd rather map those keys yourself, uninstall the 'kmilo' program. This plugin causes this behaviour.

---

