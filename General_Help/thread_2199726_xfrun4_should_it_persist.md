---
title: "xfrun4: should it persist?"
date: 2014-01-15
forum: General Help
---

### Post by vasa1 on 2014-01-15
I can press **Alt**+**F2** to bring up xfce's application finder, aka **xfrun4**, to launch a program. But after the program is launched and the application finder window "disappears", I'm seeing that xfrun4 persists in the task manager.

Is that normal? Do other users see the same thing?

---

### Post by Bucky Ball on 2014-01-15
What release are you using vasa1?

I just launched a program with alt+F2 and see no task manager. I am using 14.04 though, minimal install with xfce4 desktop environment so will be a bit different. Where is the task manager?

---

### Post by Dennis N on 2014-01-15
It's the default setting. To change:

Open "Application Finder" from Menu: Accessories > Application Finder
Preferences > Behaviour > uncheck "keep running instance in the background"

My reference is Xubuntu 12.04

---

### Post by vasa1 on 2014-01-15
> **Dennis N said:**
> It's the default setting. To change:

Open "Application Finder" from Menu: Accessories > Application Finder
Preferences > Behaviour > uncheck "keep running instance in the background"

My reference is Xubuntu 12.04

Aha! Thank you. That explains it :)

@Bucky Ball, sorry for being unclear. I meant that I could see the *xfrun4* process in the task manager. My OS is quite a mix of Lubuntu/Xubuntu with Openbox but all from 13.10.

---

