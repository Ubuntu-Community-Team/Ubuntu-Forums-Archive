---
title: "need a few tweaks for 12.10"
date: 2012-10-24
forum: General Help
---

### Post by X D face me on 2012-10-24
hey everyone

i have a few things i want to disable/change in gnome3

[LIST=1]
[*]I have two screens set up, one is my laptop and the second is my external monitor. My monitor stands left from my laptop. Now, when i move the mouse outside my laptop screen at the right side it goes to the left side of my desktop screen, is there a possibility to make that when i move the mouse out of the laptop screen at the left side, it enters my monitor at the right side?
[*]the dimensions of my laptop screen are 1360 × 768 (16:9) but the dimensions of my monitor are 1024 x 768 (4:3). when i edit the screen size settings i can easily set the right side for my laptop screen but i´m unable to edit my monitors resolution. is there any way to edit that?
[*]is there a way to disable the slide lockscreen that apears after locking my laptop? i hate the slide up unlocking and it makes my comparing ubuntu with windows 8...
[*]is there a way to move the red cross at the right top corner of a window to the left top corner in gnome3? i knew that this was easily possible with ubuntu tweak but i can´t find the setting anymore.
[/LIST]

i´ve installed ubuntu using an install dvd.
thanks to everyone who can help me

X D face me

note: i´m not very good at englisch, please suggest corrections if you can make any.

---

### Post by mc4man on 2012-10-24
Don't have multiple screens so can't help there
As far as moving the close button, very easy
Open dconf-editor
It's in org.gnome.shell.overrides, just click in the Value area & move semi-colon to the right side as in screen, 
(if desired you can also add any of the other 2 buttons, minimize & or maximize, I use this for Gs
close,minimize:

Or from command line
```
gsettings set org.gnome.shell.overrides button-layout close: 
```

Or for 2 buttons
```
gsettings set org.gnome.shell.overrides button-layout close,minimize:
```

---

### Post by X D face me on 2012-10-26
installed ubuntu again and everything is fixed, thread can be closed

---

### Post by dino99 on 2012-10-26
> **X D face me said:**
> installed ubuntu again and everything is fixed, thread can be closed

Its good that your wishes are satisfied now, but you only can mark that thread as SOLVED as its yours, simply click the Thread Tools on top right of that thread.

---

