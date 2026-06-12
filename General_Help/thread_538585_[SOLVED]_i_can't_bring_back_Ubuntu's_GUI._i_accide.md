---
title: "[SOLVED] i can't bring back Ubuntu's GUI. i accidentally broke it. please help."
date: 2007-08-30
forum: General Help
---

### Post by patambrosio on 2007-08-30
help.
i did this..

[INDENT]sudo apt-get **autoremove **librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev[/INDENT]

because i was trying to install gnome-dock, but changed my mind.
i don't know what other packages it removed.
[SIZE="2"]i broke the GUI, i can only see the terminal.[/SIZE]

i tried installing those again, and even nautilus-*, but still no luck.

i'm an absolute beginner, and i don't want to stop trying now.
[SIZE="2"]*any ideas on how to bring it back?*[/SIZE]

thanks in advance.

---

### Post by sdowney717 on 2007-08-30
sudo apt-get install gnome
try and see

---

### Post by gtdaqua on 2007-08-30
or even try this if u want a KDE environment

sudo apt-get kubuntu-desktop

this will install all necessary dependencies to get a cool looking desktop.

---

### Post by patambrosio on 2007-08-31
thanks for the help guys, it's back to normal now. :)

---

