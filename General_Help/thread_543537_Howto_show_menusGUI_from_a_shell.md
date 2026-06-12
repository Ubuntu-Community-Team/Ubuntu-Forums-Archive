---
title: "Howto: show menus/GUI from a shell?"
date: 2007-09-05
forum: General Help
---

### Post by johann_p on 2007-09-05
I know there is at least one command that will allow to show graphical yes/no prompts, menu selections etc. from within a bash shell, but I cannot remember what it was.

Can anyone help me remember? 

I often find that I *know* there is some command or app that does what I want, but it is hard to find them among the 1000s of programs that are either already installed or available for installation.

---

### Post by lloyd_b on 2007-09-05
> **johann_p said:**
> I know there is at least one command that will allow to show graphical yes/no prompts, menu selections etc. from within a bash shell, but I cannot remember what it was.

Can anyone help me remember? 

I often find that I *know* there is some command or app that does what I want, but it is hard to find them among the 1000s of programs that are either already installed or available for installation.

I *suspect* that you're talking about "dialog".  "dialog" is a program that generates assorted types of dialog boxes in a command-line environment.  Install the package "dialog", and then "man dialog" for info on how to use it.

Lloyd B.

---

### Post by johann_p on 2007-09-05
That is exactly it! There seem to be variants "gtkdialog" and "xdialog".
xdialog is the one I seem to have used years ago.
Thanks for the quick help!

---

