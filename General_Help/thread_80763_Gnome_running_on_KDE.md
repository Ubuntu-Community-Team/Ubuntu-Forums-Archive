---
title: "Gnome running on KDE"
date: 2005-10-22
forum: General Help
---

### Post by faeros on 2005-10-22
I just switched to KDE from gnome.  I used "aptitude install kubuntu-desktop" to switch.  When I resarted my system, I had a the kubuntu login, and then it went to my gnome desktop with both gdm and kdm applications....

Where did I fail?

:confused:

---

### Post by Xian on 2005-10-22
Did you select KDE in the sessions menu of GDM/KDM or just login w/default?

---

### Post by faeros on 2005-10-22
after I installed the kubuntu desktop, it prompted me in the terminal to choose between kdm/gdm.  i choose kdm.  

On the login screen there was no choice??????

---

### Post by shinygerbil on 2005-10-23
There should be a button just below the password entry box, with the options Default, Previous, KDE or Gnome. Perhaps it's set to Previous, in which case you'll end up with Gnome. Otherwise, you could try "dpkg-reconfigure kdm" as root/superuser, to check that KDE is the default.

Unfortunately, you'll end up with both KDE and Gnome apps on your desktop, which is quite annoying, but once you get the hang of the K Menu Editor it shouldn't be too much of a problem.

---

### Post by Sirin on 2005-10-23
[QUOTE=faeros]I just switched to KDE from gnome.  I used "aptitude install kubuntu-desktop" to switch.  When I resarted my system, I had a the kubuntu login, and then it went to my gnome desktop with both gdm and kdm applications....

Where did I fail?

:confused:[/QUOTE]

There is a similar thread here, [http://ubuntuforums.org/showthread.php?t=80559](http://ubuntuforums.org/showthread.php?t=80559)

---

