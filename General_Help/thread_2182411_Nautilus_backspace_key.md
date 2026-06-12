---
title: "Nautilus backspace key"
date: 2013-10-21
forum: General Help
---

### Post by makitso on 2013-10-21
So, I am using Ubuntu Gnome 13.10.  Everything is cool except Nautilus.  The backspace key appears to not work.  I looked at various earlier solutions but they did not work.  Is this a bug or feature?
BTW, did try Nemo but did not like some of the issues it created (could not get rid of the Home and Computer icons from the desktop).

---

### Post by mc4man on 2013-10-21
No idea what solutions you looked at, to enable - 
```
 gedit .config/nautilus/accels
```
at the bottom add this (no ; like other entries
```
(gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")
```
save, then stop/restart nautilus
```
nautilus -q
```
open nautilus by any avail. means

(the current is alt+arrow key(s)

---

### Post by makitso on 2013-10-21
Yes, that was the first thing I tried but it did not work :-(

OK, it does work but requires that you use the <alt> arrow keys. This does not resolve my original question of that the <Backspace> key does not work.

---

### Post by mc4man on 2013-10-21
Works here both in a unity & gnome-shell session
I'd try setting up a new user account, log in to that user, make change, ect. & see if it works
If not then maybe something specific to to a ubuntu-gnome install (which I don't have

---

### Post by makitso on 2013-10-21
For what its worth,  this does not work for both my clean install Thinkpad T60 and a VirtualBox install.  A new user did not change things.

---

### Post by coffeecat on 2013-10-21
I can confirm that the fix posted by mc4man works for me in 13.10/Unity, as it did in 13.04.

@makitso, I'm sure you got this right, but did you remember not to include a semicolon ( ; ) at the beginning of the line to be added?

---

### Post by makitso on 2013-10-22
:(  LOL, I did put the semicolon at the beginning of the line.  Dah!

Tried it just now and it did not make any difference. :-(

---

