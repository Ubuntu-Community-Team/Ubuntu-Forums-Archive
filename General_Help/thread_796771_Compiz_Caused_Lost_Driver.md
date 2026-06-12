---
title: "Compiz Caused Lost Driver?"
date: 2008-05-16
forum: General Help
---

### Post by Puptentacle on 2008-05-16
I set up Compiz for the first time today under Hardy. Everything worked fine until I did a restart. Now, the screen is in a low-res mode and when I start compiz I get the following 

```
pup@pup-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

System>Preferences>Screen Resolution is now only showing three modes, none of which are 1280 x 800 which is what I was using before and only gives a refresh rate of 61 hz. Defaulting to 1024x768. Seems to be defaulting to VESA driver. 

It also gave an error at boot about being unable to find driver. What did I do, and how do I fix it?

HP DV2550SE laptop
2GB ram
Fully updated Hardy.
gnome, but also showing same symptoms in openbox.

EDIT: Went into grub and did FixX and that did the trick. I'll leave this in case anyone else has the problem. Anyone have a clue as to WHY that would have happened?

---

