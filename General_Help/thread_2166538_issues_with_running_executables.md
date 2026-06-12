---
title: "issues with running executables"
date: 2013-08-09
forum: General Help
---

### Post by SirGuineaPig on 2013-08-09
I am having issues running linux executables (.bin, .run, .x86, etc). I tried to open up an executable .sh file in medit, and every time I try to run an
executable file, it has it listed as "Open with medit" now. I was wondering how I could make it an executable file again?

---

### Post by SweetAurora on 2013-08-09
You have to run the program in a terminal or manually create a .desktop file that points to and executes the file.

---

### Post by SirGuineaPig on 2013-08-09
Thank you! I did not know how to make a .desktop file, sorry.

---

### Post by Dennis N on 2013-08-09
Before trying to make a .desktop file, it's probably a good idea to start it from the terminal first to see how well (and if) it works.

1) be sure the program file itself has permissions set to executable (or it can't run).
2) start the terminal, and enter the full path to the program (beginning at /). Press Enter and it should run.

Desktop files:

These take some practice and study. Lots of examples of these in **/usr/share/applications** where most of them live. You may be able use these as a guide. 

The full daunting technical details are here: **[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)**

---

