---
title: "Switching Themes . . ."
date: 2008-06-01
forum: General Help
---

### Post by StupendousMan on 2008-06-01
Hello all, Mr. Newbie here.  I finally got all the eye-candy installed and working. And I am currently using Emerald for theming the windows. However, it seems that Emerald mainly handles glass-like skins, but I want to use some of the themes that I have seen under Metacity.  So am I able to switch back and forth between using Metacity & Emerald themes? And if so, how? I've tried to do it and it seems that it's either not possible or I'm doing something wrong, and my guess is that it the latter.  So any and all guidance is appreciated.  Thanks!

---

### Post by rainwalker on 2008-06-01
You can use the commands ```
metacity --replace
``` and ```
emerald --replace
``` to switch between them. I believe there's something called fusion-icon you can install that will sit in your system tray and lets you manage all sorts of settings, check it out (it's in the repositories so you can install it via System > Adminsitration > Synaptic Package Manager).

---

### Post by Forlong on 2008-06-02
'metacity --replace' will kill Compiz altogether.

The proper command to get Metacity boarders on Compiz is
```
gtk-window-decorator --replace
```

---

### Post by rainwalker on 2008-06-02
> **Forlong said:**
> 'metacity --replace' will kill Compiz altogether.

The proper command to get Metacity boarders on Compiz is
```
gtk-window-decorator --replace
```

Ah, well thank you :)

---

