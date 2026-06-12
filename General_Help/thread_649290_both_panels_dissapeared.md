---
title: "both panels dissapeared"
date: 2007-12-24
forum: General Help
---

### Post by leelandmiller on 2007-12-24
i don't know what happened.

i had two workspaces or whatever they're called and i switched to one of them.
then, where my top and bottom panels used to be, it started flashing, then they dissappeared.


how do i get them back?

---

### Post by ~LoKe on 2007-12-24
alt+f2
```
killall gnome-panel && gnome-panel
```

---

### Post by leelandmiller on 2007-12-24
Alt+F2 didn't work.
they're still gone

---

### Post by ~LoKe on 2007-12-24
ctrl+alt+F1
Log into the virtual terminal, once you've done so, type the following:
```
killall gnome-panel
```
After that is successful...
ctrl+alt+F7

---

### Post by leelandmiller on 2007-12-24
kk that didn't work either it just says gnome-panel: no process killed


wtff this is gay

---

### Post by dlegend on 2007-12-24
Try the following:

ctrl+alt+F1
Log into the virtual terminal, once you've done so, type the following:

```

gnome-panel

```

After that is successful...
ctrl+alt+F7

Basically same as ~LoKe said except it should restore the panel. The step LoKe said was to ensure the gnome-panel wasn't running if it was in-fact invisible somehow.

---

### Post by adam.tropics on 2007-12-24
> **dlegend said:**
> ...
Basically same as ~LoKe said except it should restore the panel. The step LoKe said was to ensure the gnome-panel wasn't running if it was in-fact invisible somehow.

As ~Loke said, killall gnome-panel will restart it.

---

### Post by dlegend on 2007-12-24
> **adam.tropics said:**
> As ~Loke said, killall gnome-panel will restart it.

Ah, thanks for the correction. I try to give advice but still am somewhat new to this.

---

### Post by adam.tropics on 2007-12-24
No worries. Since gnome panel is in your gnome-session with a style of 'restart', then whenever the process is killed, it will restart. Take a look at your system-->preferences-->session and look at the Current Session tab, which graphically shows this. For a little more, have a [read here]("http://www.gnome.org/learn/users-guide/latest/prefs-sessions.html"). Relevant bit about 2/3 down the page!

---

### Post by Tyke91 on 2007-12-24
have you tried rebooting your computer?

---

### Post by leelandmiller on 2007-12-25
none of that stuff worked.

i started a session in Safe-mode GNOME or something like that. and the panels were back.

---

### Post by Kulgan on 2008-01-07
Same problem, as far as I can tell, and same results. Panels are there, but not visible. I can click around and start apps from them, but not see the panels themselves. In a failsafe session, they are both there, but when I log into just "GNOME", they are gone. 

And yes, I have tried rebooting, a number of times... What scripts does the failsafe not start that I can get rid of? Everything seemed to work perfectly in failsafe. Makes me wonder why all sessions aren't like that :confused:

EDIT:
After a few reboots in and out of failsafe, it's now working in the default session. Yay

-K

---

