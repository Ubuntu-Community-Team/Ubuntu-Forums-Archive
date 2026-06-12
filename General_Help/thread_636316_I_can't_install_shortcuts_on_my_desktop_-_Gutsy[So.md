---
title: "I can't install shortcuts on my desktop - Gutsy[Solved]"
date: 2007-12-09
forum: General Help
---

### Post by digitalwave43 on 2007-12-09
First of all, I'm a N00b when it comes to linux.  I haven't played with it in years.  But here's my problem and I hope you can help me out!

I am not able to add any shortcuts to my desktop anymore.  I right click on the desktop and I usually get an option to add an application or a shortcut to it. I don't get that "pop-up" anymore.  The last time I remember it working was before I tried the whole xscreensaver trick to have the glmatrix screensaver be my desktop.  After that, I wasn't able to put up any shortcuts or have that "pop-up" come up.

Any suggestions or tips for me?  I am using Ubuntu 7.10.

Edit:  I also can't click and drag on my desktop.  Don't know why.

---

### Post by chrisccoulson on 2007-12-09
It sounds like you don't have Nautilus drawing your desktop.

In a terminal, run:
```
gconf-editor
```

Navigate to /apps/nautilus/preferences

Make sure that *show_desktop* is checked

You might need to restart Nautilus for this change to take effect:
```
killall nautilus
```

---

### Post by digitalwave43 on 2007-12-10
That was it!  Thanks a lot for your help!

---

