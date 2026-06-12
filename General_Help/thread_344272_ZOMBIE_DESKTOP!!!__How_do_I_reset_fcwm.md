---
title: "ZOMBIE DESKTOP!!!  How do I reset fcwm?"
date: 2007-01-22
forum: General Help
---

### Post by Blofeld on 2007-01-22
I have Xubuntu 6.10 installed over here.
Yesterday I loaded a program over the internet.  After I rebooted I chanced upon what I call a zombie desktop:  totally blank, those menu bars on top and bottom are gone, other than that the system works fine, as in that I can still run programs via the <Alt>-<F2> command line (that's how i connected to the internet and started Firefox).
Basically I'd either like to uninstall that last package, or just reset fcwm (at least I guess that's the piece of software that's playing up).
This is so enerving, please help me!

---

### Post by WiseElben on 2007-01-22
I'm not sure what window manager you're using, but if it's XFCE (because you said you are using Xubuntu, though you also said "fcwm"), run this in the terminal:

```
xfce4-panel &
```

You might need to add that in the startup sessions.

---

### Post by Blofeld on 2007-01-22
Yes!!!  Result!!! Thank you!!!
I love you and want to have your baby!!!
Even if it's against the laws of nature -- hey, they're fun to meddle with.
:guitar: 
But seriously, thank you, WE!

---

