---
title: "Can I Safely Rmove or Inactivate Plymouth?"
date: 2013-07-07
forum: General Help
---

### Post by Peripheral Visionary on 2013-07-07
I want to try something just for fun.  When I boot up my old desktop with Xubuntu 12.04 on it for a friend, I don't want her to know it's Xubuntu (until I'm ready to tell her, "guess what?  You're using Linux!").

I have "splash" set to "none" in my settings, but on boot-up (**I use auto-login**) I'd like to skip the pretty blue Xubuntu screen that usually appears before my desktop does.

Is there a quick little un-doable script I can write or something to comment out in the existing start-up script?  Or if I just remove Plymouth will it mess anything up? 

I just to hide Xubuntu's identity from a friend and do "the Big Reveal" later.

---

### Post by ohnonot on 2013-07-09
```
sudo gedit /boot/grub/grub.cfg  /etc/default/grub
```
remove all occurences of 'splash'.

---

### Post by jimingkui on 2013-07-09
Try Plymouth Manager, a GUI tool with the option to disable/re-enable the splash screen.

It's old but it works.

[https://launchpad.net/plymouth-manager](https://launchpad.net/plymouth-manager)

---

### Post by ohnonot on 2013-07-10
re-reading your first post, it's probably not plymouth you are talking about.
plymouth generates the boot-up screen (usually with some progress bar).
after that it goes to the display manager.
i *think* it displays a splash screen even when set to auto login.
the display manager for xubuntu would be... think, think, ...lightdm?

---

### Post by Peripheral Visionary on 2013-07-11
Wonderful, thank you!!  This will be fun!  I'll mark it SOLVED and thank both of you very much!

Oh, side note:  Gedebi was not installed by default in my Xubuntu 12.04 like it used to be in Lucid.  For anyone else reading this, gedebi can be downloaded from the repositories and used to easily and graphically install downloaded .deb files like Plymouth Manager.

Thanks again, both of you!

---

