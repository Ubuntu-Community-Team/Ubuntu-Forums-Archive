---
title: "[SOLVED] Installed Wrong Keyboard Layout...."
date: 2007-07-18
forum: General Help
---

### Post by ReaderRat on 2007-07-18
Hey Guys,
I accidently installed the wrong KB layout when I installed Feisty. I can't make heads or tails out of my KB. I  did manage to ```
sudo dpkg-reconfigure xserver-xorg 
``` but that just made things worse. I changed (put the RIGHT video card, refresh rates, etc. in the reconfigure) and now Xserver is messed up. All this was working, except the KB beforehand. I am going to do one more dpkg-reconfigure and try to put the values back that I changed. That may get my video back, 

If it does, how do you restart X from the CLI? How do you install the English KB?

I really don't want to re-install Vista & Ubuntu AGAIN.

Thanks for any help..................ReaderRat

---

### Post by ReaderRat on 2007-07-18
OK Guys, (and Gals),
I got my video back. Now how do I get rid of the current KB (don't know what it is), and How do I install the eng- version KB?

---

### Post by strabes on 2007-07-18
I don't know how to change it system-wide (for the tty#s, etc) but you can just go to the keyboard layout section of gnome to change it for the GUI. Maybe you selected dvorak? You should consider switching.

---

### Post by dpar on 2007-07-18
Did you try System>Preferences>Keyboard

---

### Post by djchandler on 2007-07-18
> **dpar said:**
> Did you try System>Preferences>Keyboard

You may want to also look at System>Administration>Language Support.
It's the gnome icon that looks like a blue flag on a flagpole waving in the wind.

---

