---
title: "Can someone teach me the art of Symbolic Links &amp; what they are useful for."
date: 2006-08-23
forum: General Help
---

### Post by UltraSonicSite on 2006-08-23
I hear of alot of problems pertaining to Symbolic Links, I don't believe I've had any yet, then again I wouldn't know because I never solved the problems that I assume were related to symbolic links.

-Anyway, can someone explain to me the usage of symbolic links? What they are useful for? How do I use them?

---

### Post by K.Mandla on 2006-08-23
I use them like a shortcut or an alias. For example, I have a modular drive in my laptop and it is usually assigned to /dev/hdc1. I set up fstab to mount that drive to /media/modular. 

In my home directory I have a link called ~/modular that points to /media/modular. So when I double-click on ~/modular, I'm taken to the second hard drive.

Does that make sense? 

I'm sure there are lots of other uses, but that's the first one that comes to mind for me.

---

### Post by bukwirm on 2006-08-23
A symbolic link is similar to a Windows shortcut (kind of) Read [this]("http://en.wikipedia.org/wiki/Symbolic_link") for more details.

See the ln man page, also.

---

### Post by szf on 2006-08-23
[http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)
Explains everything I know about them and a bit more...

---

### Post by UltraSonicSite on 2006-08-24
Thanks alot guys.

---

