---
title: "How to set up this alias?"
date: 2006-07-11
forum: General Help
---

### Post by cnbiz850 on 2006-07-11
I would like to alias emacs such that whenever I type "emacs foo" it is actually "emacs foo&".  I tried in ~/.bashrc the following but it doesn't work:

alias emacs='emacs &'

---

### Post by ciscosurfer on 2006-07-11
Try going to the original emacs binary file (w/in a gui), right-clicking, and adding your command to the command entry.  I believe it's under /usr/bin/emacs
If not, then in a terminal, do a search for emacs to locate it:```
sudo updatedb
[I]wait for updatedb to finish...then issue:
[/I]locate emacs
``` :D

---

### Post by cnbiz850 on 2006-07-11
> **ciscosurfer said:**
> Try going to the original emacs binary file (w/in a gui), right-clicking, and adding your command to the command entry.  I believe it's under /usr/bin/emacs
If not, then in a terminal, do a search for emacs to locate it:```
sudo updatedb
[I]wait for updatedb to finish...then issue:
[/I]locate emacs
``` :D

Sorry, I don't quite understand what you mean.  I do use /usr/bin/emacs and just try to make it run in the background (not tying up the xterm).

---

### Post by scxtt on 2006-07-11
try making an alias like this:
[indent]alias emacs='emacs $1 &'[/indent]in your .bashrc ...

---

### Post by ciscosurfer on 2006-07-11
Link emacs to your desktop and run it from there.  No need to enter a terminal to start up emacs.  Alternatively, add emacs to your Ubuntu Menu > Editors menu.  Then if you like, right-click and add emacs as a laucher to your top panel.

---

### Post by cnbiz850 on 2006-07-11
> **scxtt said:**
> try making an alias like this:
[indent]alias emacs='emacs $1 &'[/indent]in your .bashrc ...

With this, 'emacs foo' reports: bash: foo: command not found.
Doesn't work.

---

### Post by cnbiz850 on 2006-07-11
> **ciscosurfer said:**
> Link emacs to your desktop and run it from there.  No need to enter a terminal to start up emacs.  Alternatively, add emacs to your Ubuntu Menu > Editors menu.  Then if you like, right-click and add emacs as a laucher to your top panel.

Well I could do that, but sometimes it is not convenient when I am in a terminal in a specific directory.

---

### Post by scxtt on 2006-07-11
> **cnbiz850 said:**
> With this, 'emacs foo' reports: bash: foo: command not found.
Doesn't work.yeah, i guess that was more or a script notation than how an alias would work ...

---

