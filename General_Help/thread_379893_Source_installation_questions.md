---
title: "Source installation questions"
date: 2007-03-09
forum: General Help
---

### Post by Ptero-4 on 2007-03-09
Hi. I`m trying to install some software from sources (to make some modifications to it), 
I took one of the apps using apt-src to download the sources from the source (deb-src) repositories and need to change the "debian" stuff so that the package manager thinks it is a version later than what is in the repos (to keep apt from "updating" it with the original version without having to "keep" or "hold" it in it`s current version), the other is from the web. And I wanted to know:

1. How to make the mods to the "debian" stuff?
2. How do I make to get a .po file (i18n stuff) recognized and used during compilation?

---

### Post by nanotube on 2007-03-09
to prevent upgrades, the best way would be to install the package as is, and then go to synaptic and select that package choose "lock version". that way it won't try to update.

don't know about that .po stuff. :)

---

### Post by Ptero-4 on 2007-03-09
The problem nanotube, is that if I "lock" a package the update manager will always ask me to update it and I don`t want that package showing up in the update manager at all.
As for the po file, well .po files are the files holding the text strings that will be added to a program when you compile it, I asked because I found a .po file for my native language (Spanish) but it`s a loose .po file and it`s not included in the source tarball.

P.D: I`m not installing the binary package, I`m installing from the sources using apt-src, which have the side-effect that apt will always try to replace my custom built deb with the binary one from the repos (which is what I want to avoid).

---

