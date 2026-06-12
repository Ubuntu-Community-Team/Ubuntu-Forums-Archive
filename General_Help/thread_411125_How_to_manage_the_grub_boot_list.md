---
title: "How to manage the grub boot list"
date: 2007-04-16
forum: General Help
---

### Post by TedyBear on 2007-04-16
How do I manage the list of choices from which to boot at startup? I have noticed that there have been more entries added over time (every new installed kernel-image) and now it has gotten frustratingly long.

I would like to remove some of the older entries as they are now obsolete. I am more used to lilo.

---

### Post by namityadav on 2007-04-16
Edit the /boot/grub/menu.lst file for the choices that you want to see at the time of boot up.

Don't forget to make a backup though :-)

---

