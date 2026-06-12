---
title: "Re-mapping the alt keys and virtual terminals"
date: 2006-12-02
forum: General Help
---

### Post by g4c9z on 2006-12-02
Hi,

I'm trying to map my alt keys to each do something different.  I assume xmodmap is the command to use to do that.

My original listing of modifier keys is as follows:

```
adam>xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

```
I notice the two copies of Alt_L being mapped to 2 different keycodes, which seems strange and which may be related to my problem.

My goal is to get right alt key to mean Mod3, and the left one to remain doing what it usually does.  I first tried to simply assign the right alt key to Mod3:

```
adam>xmodmap -e "add Mod3 = Alt_R"
adam>xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3        Alt_R (0x71)
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

```
This appeared to work; left alt still opens menus, and right alt doesn't.  But for some reason when I push Ctrl+Alt+F1 to switch virtual terminals after making that change, nothing happens; whereas it works fine before the change.  I've tried it with 2 different window managers and the same problem occurs, so it probably isn't the window manager's fault.

So, am I doing anything wrong here, and why is it blocking my virtual terminals?

---

### Post by joshuapurcell on 2006-12-16
I'd like to know why there was a change to the ALT and CTRL key mapping in Edgy, what exactly those change are, and how we can revert to the old keymap if we need/want to. I haven't been able to find that information yet, and I'm getting tired of having to constantly use only the left ALT and CTRL keys. I'll be looking for the answer, and I'll post once I find it. Here's another thread on the same subject:
[http://ubuntuforums.org/showthread.php?t=291363](http://ubuntuforums.org/showthread.php?t=291363)

---

