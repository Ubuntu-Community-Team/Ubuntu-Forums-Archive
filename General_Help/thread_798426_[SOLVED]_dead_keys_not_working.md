---
title: "[SOLVED] dead keys not working"
date: 2008-05-18
forum: General Help
---

### Post by Fibonacci on 2008-05-18
Hello,

Since about yesterday, dead keys do not work on most (almost all) programs on my system. That is, if I type e.g. dead_acute + a it comes out as ´a, instead of á. The Compose key is ignored in the same fashion, so e.g. Compose+'+a produces 'a instead of á.
The programs in which this problem appears include Firefox, Epiphany, Gnome Terminal, Gedit, and Tcl/Tk shell -  in fact, the only program so far in which I've found the dead keys to work as they should is Mathematica.

With respect to Gnome Terminal, there is a way to make dead keys work - namely, to switch the input method from "System" to "Simple". Unfortunately most apps do not have such an input method switcher, so I still cannot write accented characters on Firefox or aMSN (which is Tcl/Tk-based).

Also, when running the same apps (exact same binary files) under a Hardy liveCD, dead keys work fine on all of them.

Any help with this would be greatly appreciated.

-Fibo

---

### Post by techstop on 2008-05-18
Have you tried resetting your keyboard preferences to use dead keys?

System>Preferences>Keyboard>Layouts

Add a layout using deadkeys if there is not already one there...

---

### Post by Fibonacci on 2008-05-18
> **techstop said:**
> Have you tried resetting your keyboard preferences to use dead keys?

System>Preferences>Keyboard>Layouts

Add a layout using deadkeys if there is not already one there...

Yes I have. In fact the layout I'm currently using does use dead keys - but they do not work.

---

### Post by Fibonacci on 2008-05-18
Update: dead keys work fine for new user accounts, but are still not working on my account.

---

### Post by Fibonacci on 2008-05-18
I finally solved it. It was all due to a symlink on ~/.xinput.d which pointed to /etc/X11/xinit/xinput.d/scim. I just removed it, and now dead keys work fine everywhere.

---

### Post by tasuki on 2010-07-02
> **Fibonacci said:**
> I finally solved it. It was all due to a symlink on ~/.xinput.d which pointed to /etc/X11/xinit/xinput.d/scim. I just removed it, and now dead keys work fine everywhere.

YÓU ÁR&#282; MÝ HÉRÓ!

I've had this problem for ages, never knew why. I knew it was some hidden config file, as it worked for other users. Thank you, thank you, thank you!

---

### Post by michopop on 2010-12-23
my hero as well...

a question. in folder /etc/X11/xinit/xinput.d/ I have the following files: all_ALL  default-xim  ja_JP  lo-gtk  none  th_TH default ibus  zh_CN  zh_SG ko_KR  lo_TH   th-gtk  th-xim  zh_HK  zh_TW. is it safe to delete all this? 

background: before i had by mistake installed scim (with all asian stuff...). after uninstalling it - the dead keys stoped working. i deleted first the "scim" file. nothing happened. then i deleted "scim-bridge" and "scim-immodule". then it worked!

---

