---
title: "[SOLVED] CTRL+ALT+BACKSPACE Oddity"
date: 2008-03-19
forum: General Help
---

### Post by vahnx on 2008-03-19
Some times when I press CTRL+ALT+BACKSPACE then go to log back in, I will hear the Ubuntu login sound but I will not see anything and i can just move my cursor. Is that because 'nautilus' crashes and I have to manually press F7 (or whatever those terminal keys are) and start nautilus?<--- (just thought of that now but I'm not sure if it would work) 

Would this happen because Ubuntu is thinking secretly and all of a sudden I kill it? And is CTRL+ALT+BACKSPACE the equivelent of logging off, or would using Log Out be a better solution? If so, I would like to bind Log Out to CTRL+ALT+BACKSPACE.

Thanks.

---

### Post by Happy_Man on 2008-03-19
In Linux, everything graphical runs on top of an program called X. So when you press ctrl-alt-backspace, you are not logging out, but rather killing the application the GUI is running on. If it helps, the chain looks like this:
X > GDM (login/gnome manager) > GNOME desktop/applications

So ctrl-alt-backspace is a quick and easy way to kill GNOME if it's frozen. But then, sometimes, you get issues like this. It's just because you aren't killing GNOME the right way. It's somewhat akin to holding down the power button to shut off the computer; eventually, you will get issues. Moral of the story: Don't use it unless necessary. :D

---

