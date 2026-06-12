---
title: "Remove Old Kernels"
date: 2019-06-04
forum: General Help
---

### Post by doommarine on 2019-06-04
Hi What a mess...
Why they kill all the nice things ...

GKSU is not working anymore...
Ubuntu Tweak is not working ...

I realy tink about a downgrade ...

Please you explain how to clean out all the old kernels and kernel sources for people who are just user and not programmers?

... I am a user and I will need a GUI based programm ... and I do not want to learn all the same again and again after a couple of years...

Thank you.
Michael.

---

### Post by Frogs Hair on 2019-06-04
Post moved to a current thread.

---

### Post by cruzer001 on 2019-06-04
in terminal
```
sudo apt autoremove
```
If that doesn't work I would get a refund.

---

### Post by deadflowr on 2019-06-04
I'm not sure I've set anything beyond the default, but just running updates through Software Updater will now give you an option to also remove old kernels.
Typically it'll look like this old image
[ATTACH=CONFIG]283379[/ATTACH]
This is an image from an [old thread I posted in a year ago]("https://ubuntuforums.org/showthread.php?t=2396626"), but still relevant.

---

### Post by TheFu on 2019-06-04
If you don't want to learn stuff in a new way every few years, then pick a GUI and stick with it.  I'm using the GUI I used in 1996, fvwm2.  It mostly works and looks the same.

If you stay away from the latest and greatest GUI stuff, then changes happen much more slowly.  KDE and Gnome3 are the hot, new, GUIs.  They will continue to change for the next few years.

Also, if you learn how to do things without the GUI, commands change very slowly.  Many of my scripts from the early 1990s still work the same today. Most commands have exactly the same syntax over the last 20+ yrs, but a few administrative commands have completely changed.
```

sudo apt autoremove
sudo apt autoclean
```
You can replace "apt" with "apt-get", if you prefer.
It is much easier for us to post those commands than spend 30 minutes typing and clipping images.

---

