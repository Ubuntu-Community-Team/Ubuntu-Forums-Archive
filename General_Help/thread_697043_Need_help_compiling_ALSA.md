---
title: "Need help compiling ALSA"
date: 2008-02-14
forum: General Help
---

### Post by malfist on 2008-02-14
I can compile and configure alsa-driver alsa-utils and alsa-libs just fine, but it doesn't install them were the need to go. For example, after compiling and make installing alsa-utils (which includes alsamixer) I type the command, alsamixer. Bash tells me it can't find it but I can install it with apt-get install alsa-utils. However I can run it by going to /usr/src/alsa/alsa-utils-1.0.16/alsamixer/alsamixer.

How can I get this to install where it is supposed to? I'm assuming it is the reason I don't have alsa, even though I've compiled and make installed it.

---

### Post by malfist on 2008-02-14
It seems it did install it, somewhat. I have the alsa driver, and double clicking on the volumn control brings up gnomes alsamixer, but it still shows everything as muted (although it's not). I can play sound, but still have to go to /usr/src/.... to run alsamixer.

Any advice?

---

### Post by este on 2008-02-14
Maybe because you are installing two different versions ?  I'm assuming 16 from their site and 14 from installer ?

I posted on your other thread, but I really have no idea - I've got my own problems with alsa :)

---

### Post by malfist on 2008-02-14
What do you mean? 14 from what installer? I complied everything by hand and did not use an installer. Also, how can I make aptitude and apt-get think I have alsa? I have to manually startx after boot because I can't reinstall gdm, gdm-themes, or fast-applet-user-switcher without overwriting what I have from alsa?

---

### Post by malfist on 2008-02-14
settings in alsamixer are still getting reset every reboot. :(

This may fix it: sudo alsactl store
gonna reboot and test.
Nope, wasn't saved.

---

