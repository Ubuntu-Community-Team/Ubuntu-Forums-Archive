---
title: "Gnomebaker is not working in Breezy!"
date: 2005-11-02
forum: General Help
---

### Post by galactus51 on 2005-11-02
Hi, Gnomebaker doesn't work because he says that my DVD recorder (LG GSA 4163b) is not mounted on MTAB, or some thing lake that. 

 I've tried Gnomebaker version 0.5 and did the same.
The CD-R or DVD-R it is mounted acording to the symble on my Desktop.

I'm trying to record an Audio CD, it finishes to do the convertion and when he will start to record he gives me the message about MTAB or just freeze. 

Any help?
 
Sorry about my english.

---

### Post by ecobuntu on 2005-11-02
[QUOTE=galactus51]Hi, Gnomebaker doesn't work because he says that my DVD recorder (LG GSA 4163b) is not mounted on MTAB, or some thing lake that. 

 I've tried Gnomebaker version 0.5 and did the same.
The CD-R or DVD-R it is mounted acording to the symble on my Desktop.

I'm trying to record an Audio CD, it finishes to do the convertion and when he will start to record he gives me the message about MTAB or just freeze. 

Any help?
 
Sorry about my english.[/QUOTE]

could you run gnomebaker from the terminal and post your actual error?

---

### Post by jvictor on 2005-11-02
For me on AMD 64 it segfaults even if we try to blank a cd-rw.. Graveman saved the day for me 

[http://ubuntuforums.org/showthread.php?t=84999](http://ubuntuforums.org/showthread.php?t=84999)

---

### Post by galactus51 on 2005-11-03
[QUOTE=ecobuntu]could you run gnomebaker from the terminal and post your actual error?[/QUOTE]


Ok, here it is:

galactus@Casa:~$ gnomebaker
Xlib: unexpected async reply (sequence 0x136211)!



And he freeze.

---

### Post by drunken-wallaby on 2005-11-03
[QUOTE=galactus51]Ok, here it is:

galactus@Casa:~$ gnomebaker
Xlib: unexpected async reply (sequence 0x136211)!



And he freeze.[/QUOTE]

i can back up galactus51 on this one. on my pc (and on my girlfriend's pc as well) the same error occurs (though sometimes the sequence 0x?????? differs)

greets,
bernhard

---

### Post by NoWhereMan on 2006-01-07
I get this error:
```
$ gnomebaker

(gnomebaker:11220): Gtk-WARNING **: gtkwidget.c:4205: widget not within a GtkWindow
*** glibc detected *** free(): invalid pointer: 0x0811f4b0 ***
```

---

