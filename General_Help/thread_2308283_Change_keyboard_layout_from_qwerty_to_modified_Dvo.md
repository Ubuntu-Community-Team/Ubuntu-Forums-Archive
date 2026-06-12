---
title: "Change keyboard layout from qwerty to modified Dvorak"
date: 2016-01-01
forum: General Help
---

### Post by chaaderf on 2016-01-01
Okay. Perhaps someone could help me little bit.

**Problem**
I am currenly using qwerty with some Scandinavian modifications on my keyboard. I want to change the keyboard layout such that it is not qwerty but more like a custom Dvorak one. In addition, I want to make a script (or two scripts, doesn't matter) that changes the keyboard layout when I call the script (from terminal or from menu). Please note, that I have only one physical keyboard!

**1.**
As far as I can see, the only option for me (as I want modified Dvorak) is to play somehow with
```
xmodmap -pke
```
but I can't figure out how. I can get a file which contains the qwerty layout, but is it wise to modify this file by hand to create a new layout? Also, can xmodmap read a new layout file to generate the new positions for keys?

**2.**
Once I know how to do the change manually, the script is the question. How to do the script(s) well?

Thank you for your help! ^^

---

### Post by 1clue on 2016-01-01
Are you in X or on the black screen?

I use dvorak but just set it in my control panel: System Settings->Text Entry.  In the black screen (non-gui terminal) you would use 'loadkeys dvorak'

You can modify the keys as you want, but start with what's closest.  Also it's a really good idea to always map key code to character, xmodmap lets you map character to character which can get you into a mess if you run the same command twice or more.

---

### Post by chaaderf on 2016-01-01
I am in X. (Until something happens and ruins GUI. :D ) I also tried to find something similiar as you mentioned, but failed. Maybe we have different DE.

---

### Post by 1clue on 2016-01-01
I'm using Ubuntu 15.04.  You would typically find the keyboard layout in localization or keyboard settings somewhere.  Every DE or WM has a different way of doing it, so I can't so much help with that.

---

