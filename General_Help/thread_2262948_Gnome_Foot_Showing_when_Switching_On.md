---
title: "Gnome Foot Showing when Switching On"
date: 2015-01-28
forum: General Help
---

### Post by danjswade on 2015-01-28
Hi all

This is my first time here, so sorry if I make a silly faux-pas!

I've been using Ubuntu for about a year or so now. I read about Gnome and thought I'd give it a whirl. Installed it all and worked fine. Decided it wasn't for me so removed it. Again, all went well so far.

During the process, it asked me which Display Manager to use. I opted for gdm.

But now when I switch the computer on, I get the Gnome foot every time it boots and I can't change the wallpaper (sounds silly, but it's REALLY bugging me!!)

How do I revert back to the way Ubuntu used to load (guess going back to lightdm?)>

Thanks and sorry for this being a silly question

---

### Post by philinux on 2015-01-28
Open a terminal.

```
sudo dpkg-reconfigure gdm
```

choose lightdm

Then reboot.

---

### Post by danjswade on 2015-01-31
Thanks for that, but when I do it, I get the error 

/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed

Any ideas??

---

### Post by ian-weisser on 2015-02-05
Reinstall gdm.
Then choose lightdm.

---

