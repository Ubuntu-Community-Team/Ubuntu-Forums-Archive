---
title: "Gedit always requires sudo"
date: 2013-03-19
forum: General Help
---

### Post by peterbarnett03 on 2013-03-19
Recently, I tried changing my preferences around and what not to make Ubuntu look more like a Mac. I updated some stuff and replaced some files, and it looks great. However, now whenever I try to edit some files in gedit, I always get the following warnings:

```
plbarne@ubuntu:~/Desktop/Java_Project_AB$ gedit plyDef.java

(gedit:2786): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1947:11: Not using units is deprecated. Assuming 'px'.

```

It usually still opens, but it always gives me a read only copy. The only way to fix this is to do gksudo before it, but that gets annoying, and I hate having to give my password everytime. Is there a way to get rid of this warning, get rid of having to use gksudo, and get rid of it not being read only? Thanks!

---

### Post by peterbarnett03 on 2013-03-19
Solved it myself. I think, or so it seems. Got rid of the warnings by adding px to the file. We'll see if it holds.

---

### Post by Impavidus on 2013-03-19
It seems like you're editing a file that's owned by root, so you don't have write permissions for it. [s]If you use gksudo gedit to modify it, it will certainly become owned by root.[/s] You can check ownership and permissions with```
ls -l plyDef.java
```You can change ownership back to yourself with```
sudo chown yourusername plyDef.java
```(Or substitute any other file name for which the problem occurs.)

---

### Post by QIII on 2013-03-19
Careful, now.

gksudo *avoids *having the file become owned by root if it belongs to a user.

Please read [this.]("https://help.ubuntu.com/community/RootSudo")

Look for the section "Graphical sudo".

Always use gksudo for graphical apps when you need elevated privileges.

---

### Post by Impavidus on 2013-03-19
OK, my mistake. For a moment I though that was only the case for a few config files, which is, of course, illogical.

---

### Post by QIII on 2013-03-19
I thought I made a mistake once ...

OK.  Old joke.

---

