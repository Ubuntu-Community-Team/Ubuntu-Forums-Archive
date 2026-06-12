---
title: "Start up program list file"
date: 2006-11-14
forum: General Help
---

### Post by dracule on 2006-11-14
I recently tried installing beryl on my laptop, and added the proper script under the start up manager.  Now ubuntu fails to load anything past the splash image.  In recovery mode, I can use Gnome fine, but I cant change the start up programs for my main session. Is there a file I can edit to take off beryl?

---

### Post by pay on 2006-11-14
Did you change your /etc/X11/xorg.conf? You can stop/start beryl by removing/adding "beryl-manager" to Desktop > Prefreneces > Sessions (in Gnome).

---

### Post by beerorkid on 2006-11-14
I did the same thing.

dracule and I would like to know where the file is so we can edit it to remove beryl-manager or other things from the Desktop > Prefreneces > Sessions when you cannot access it cuz of the crash.

anyways I just ```
sudo apt-get remove beryl emerald
``` and you should be able to get back into metacity, remove it from your startup until you get beryl working correctly then add it back in.

---

