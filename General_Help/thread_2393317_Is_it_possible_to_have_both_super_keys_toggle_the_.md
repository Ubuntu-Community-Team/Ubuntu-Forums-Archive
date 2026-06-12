---
title: "Is it possible to have both super keys toggle the overview?"
date: 2018-06-01
forum: General Help
---

### Post by jonathan90 on 2018-06-01
Is it possible to have both super keys toggle the overview? Gnome Tweak Tool only lets me choose the left or the right super key as the one that toggles the overview, but I'd like to have both do that. Thanks!

---

### Post by debustillo on 2018-06-22
Use xmodmap to map the same function on both key codes.
For example, on my X220 i use xev to identify my right keycode = 135. Therefore I change in ~/.Xmodmap the following:
keycode 135 = Super_L NoSymbol Super_L

Look here on how to do it: 
[https://wiki.manjaro.org/index.php/Keyboard_Layout](https://wiki.manjaro.org/index.php/Keyboard_Layout)

I'm an Arch (and former Ubuntu) user, but since we talk about the Desktop and not the distro, it should work, as well. Cross fingers! :)

---

