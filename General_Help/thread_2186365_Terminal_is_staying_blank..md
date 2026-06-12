---
title: "Terminal is staying blank."
date: 2013-11-07
forum: General Help
---

### Post by bddenhartog on 2013-11-07
Hey there, hope you guys can help me sort out an issue! I installed Guake, decided I didn't have a need for it, and uninstalled it. All of this was done via the Software Center. Now, when I launch Terminal with my shortcut keystroke or through dash, i do not get my usual prompt -- with "username $" -- it stays blank. I can type in it, but nothing happens.

Any thoughts?

Edit: The issue persists through logout and shutdown/restart.

---

### Post by steeldriver on 2013-11-07
Are you sure it's not just a color issue (foreground text and window background the same color)? That happens to me everytime I switch between gnome-terminal and xfce-terminal. You can change it via the terminal menus Edit --> Profile Preferences --> Color

---

### Post by bddenhartog on 2013-11-07
> **steeldriver said:**
> Are you sure it's not just a color issue (foreground text and window background the same color)? That happens to me everytime I switch between gnome-terminal and xfce-terminal. You can change it via the terminal menus Edit --> Profile Preferences --> Color

Absolutely positive it's not a color issue. As I said, I can type into the terminal window and see what I type, however I do not have the "username: $" prompt, and typing, pressing return, nor any other combination of keys accomplishes anything.

---

### Post by Impavidus on 2013-11-07
In other words, the terminal opens and works, but the shell doesn't give you a prompt. The last time I saw something like that on the fora it was because some command in .bashrc never returned. Maybe check your .bashrc. You could post it, many eyes see more than two.

---

### Post by bddenhartog on 2013-11-08
> **Impavidus said:**
> In other words, the terminal opens and works, but the shell doesn't give you a prompt. The last time I saw something like that on the fora it was because some command in .bashrc never returned. Maybe check your .bashrc. You could post it, many eyes see more than two.

You were absolutely right! I hadn't modified my bashrc on this installation yet, so it was pretty easy to see what was causing the issue -- RVM seemed to have added a few lines to .bashrc, .bashrc_profile, that's what was causing the issue. If I commented out the **source ~/.profile**, I received a prompt.

---

