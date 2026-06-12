---
title: "How to switch to KDM?"
date: 2006-09-09
forum: General Help
---

### Post by solarwind on 2006-09-09
Hi all,

I recently installed kde desktop from my ubuntu gnome desktop.
I did a:

sudo apt-get install kubuntu-desktop

How do I switch to KDM (K display manager)?

Thanks in advance!

---

### Post by jdong on 2006-09-09
Run **sudo dpkg-reconfigure kdm** at a terminal. When it asks you, choose kdm as the default login manager. Then, reboot.

---

### Post by solarwind on 2006-09-09
Wow thanks a lot! I never even knew about the dpkg-reconfigure program.

Thanks again!

---

