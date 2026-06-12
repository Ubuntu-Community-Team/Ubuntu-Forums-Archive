---
title: "Terminal Command Question"
date: 2008-02-25
forum: General Help
---

### Post by Kemrin on 2008-02-25
I'm looking for a terminal command that will minimize all programs, or that will minimize any programs. How do i minimize things from the terminal?

---

### Post by Nameless_one on 2008-02-25
I don't think there is a command for that, although Alt+F9 minimizes the current window.

---

### Post by Bubba64 on 2008-02-25
This question of minimizing programs is to vague, can you be more specific, I probably can't help you but the question is very broad and with a little more explanation as to what your trying to achieve you will probably get an answer from somebody who is more knowledgeable.
Good Luck

---

### Post by ryanhaigh on 2008-02-25
apparently this thread has a solution to your problem, i didn't have time to read the whole thing but its something about the wmctrl command.
[http://ubuntuforums.org/showthread.php?t=555829](http://ubuntuforums.org/showthread.php?t=555829)

---

### Post by y-lee on 2008-02-25
> apparently this thread has a solution to your problem, i didn't have time to read the whole thing but its something about the wmctrl command.
[http://ubuntuforums.org/showthread.php?t=555829](http://ubuntuforums.org/showthread.php?t=555829)

Wow that is pretty cool, I googled wmctrl to see if it would work with gnome and it seems it probably does, something to play with when i can find time. Thanks :)


[wmctrl -- Shade, move, resize windows from a shell]("http://www.oreillynet.com/sysadmin/blog/2004/12/wmctrl_shade_move_resize_windo.html")

From [wmctrl web site]("http://sweb.cz/tripie/utils/wmctrl/")


>  Please note that wmctrl only works with window managers which implement the EWMH specification. The program is known to work - either fully or partially - with the following window managers:

     [LIST]
[*]blackbox >= 0.70
[*] icewm
[*] kwin (the default WM for KDE)
[*] metacity (the default WM for GNOME)
[*] openbox >= 3
[*] sawfish
[*] fvwm >= 2.5
[*] waimea
[*] pekwm
[*]enlightenment >= 0.16.6
[*]xfce >= 4
[*]fluxbox >= 0.9.6
[*]matchbox
[*]window maker >= 0.91
[/LIST]


**EDIT:** It is in the repos too it seems. I found it in synaptic :)

---

### Post by SOULRiDER on 2008-02-25
Ctrl + Alt + D will minimize everything and how your desktop.. maybe thats remotely useful... ?

---

### Post by ryanhaigh on 2008-02-25
> **SOULRiDER said:**
> Ctrl + Alt + D will minimize everything and how your desktop.. maybe thats remotely useful... ?

If this is what you are looking for you can also modify the keboard shortcut using gconf-editor (be careful not to assign to a single letter though) or even better if you are using compiz have a look in the general settings.

---

### Post by PinkFloyd102489 on 2008-02-25
You dont even have to go into gconf or compiz, Keyboard Shortcuts in the Preferences menu will take care of it. I think it's called Hide Windows and Show Desktop.

---

### Post by ryanhaigh on 2008-02-25
> **PinkFloyd102489 said:**
> You dont even have to go into gconf or compiz, Keyboard Shortcuts in the Preferences menu will take care of it. I think it's called Hide Windows and Show Desktop.

I have always found that that app doesn't work particularly well for me when trying to set Super key combos thats why I use gconf although it may have improved in later releases.

---

### Post by Kemrin on 2008-02-25
What I'm trying to do is find a way to minimize everything at startup. I'm planning to write a script to execute at startup that will minimize everything. This is a step. Thanks everyone, you've been pretty helpful. If anyone knows a command that doesn't require a program installed, that would help. Other than that though I think I've got it back under control.

---

