---
title: "Xserver Prooblem"
date: 2007-03-08
forum: General Help
---

### Post by Joka999 on 2007-03-08
Hi i just installed Beryl everything was gd until i restarted my laptop, it said something about Xserver. Any help please?

---

### Post by ArieT on 2007-03-08
It sais something aboud Xserver... What exactly?

---

### Post by Joka999 on 2007-03-08
Erm something about configuration n it says do i wna c the diagnostics n stuff

---

### Post by zvacet on 2007-03-08
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Joka999 on 2007-03-08
Thnx for the reply i will try tht

---

### Post by Joka999 on 2007-03-09
Tried that and the log in screen came up but when i logged on it does get past the splash ting any one know whats wrong?

---

### Post by hikaricore on 2007-03-09
Not trying to be rude but I can't make sense of what you just said.

Please provide more accurate descriptions of what the issue you're having is, and the errors and such you are getting.  Making your posts readable will also go a long way towards results.

Example from what I can tell above you said:

"I tried that, and then the login screen came up.  When I logged in, it does get past the splash thing.  Anyone know what is wrong?"

Reading it like this I can't even tell there is still a problem until the last part where I'm confused as all hell.

---

### Post by Joka999 on 2007-03-09
Sorry i'm new to linux but second try yea...Right i put "Sudo dpkg-reconfigure xserver-xorg" and when i turn my laptop on i can now get to the login screen. But you know the screen where it loads can't really describe it sorry but it doesn't get past that screen. hopefully you understand that :D

---

### Post by hikaricore on 2007-03-09
It's ok, so let me see if I understand this.  After the X server failed to load last time, it dumped you back to a login prompt.  This would have been text based like a dos prompt.  There you typed "sudo dpkg-reconfigure xserver-xorg" and followed the prompts to the end saving the settings as the system detected them?  Then you rebooted and the login screen for GDM now shows up? Or a text login prompt.  If it's the graphical login screen is the system freezing there?

---

### Post by Joka999 on 2007-03-09
I login then when it loads and makes noises its freezes der but i dnt know why(thnx for helpin btw)

---

### Post by hikaricore on 2007-03-09
I'm not sure exactly how you installed beryl but from the sounds of it, what's happening is a video driver issue with the X server.  If you have an ATI card and you setup the special xserver type (which the name of escapes me at the moment) for that card, you may have to manually change it back or reverse the instructions you followed to install beryl.  The first thing you should try is to make sure your system is actually froze up by hitting ctrl+alt+f1 when the graphical login screen comes up.   If this switches you to black login screen, you'll be able to login and fix whatever is messed up manually.

---

### Post by Joka999 on 2007-03-10
Anyone got any help?

---

### Post by strabes on 2007-03-10
Did you set up a separate login session for beryl? Are you using XGL or AIGLX? Do you have an Nvidia or ATI video card? Which how-to did you use to set up beryl? Please respond without the AIM lingo and with coherent and complete sentences so I can help you as best as I can.

---

### Post by Joka999 on 2007-03-10
I didn't use a how-to i got it off the package manager and just installed and i didn't set up a seperate session and i got ATI video card.I'm not sure about XGL OR AIXGL sorry

---

