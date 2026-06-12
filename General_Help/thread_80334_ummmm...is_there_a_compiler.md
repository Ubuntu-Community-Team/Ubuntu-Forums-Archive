---
title: "ummmm...is there a compiler?"
date: 2005-10-21
forum: General Help
---

### Post by murrowman789 on 2005-10-21
since no one is replying on lq i might as well post here.


yesterday i got the latest stable version of xmms. i unzipped it, changed directories, then ./configure. it gave me a bunch of crap and then said something about there not being a compiler. (btw, this is all in terminal)

first of all, can someone please explain why ubuntu doesnt come stock with gcc or the like?

and then i need a link to a binary of gcc or the like so i can listen to music again!

i guess this is what i get for switching back and forth between this and slackware.

---

### Post by N45800 on 2005-10-21
sudo apt-get install build-essential
;)

---

### Post by murrowman789 on 2005-10-21
could you clarify that plars?

nm, i found what you were talking about on the ubuntu guide. thanks man, i hope it works.

---

### Post by aysiu on 2005-10-22
Are you trying to compile XMMS because you want to compile it or because you don't know there's an easier way to install it? If it's the former, type this in a terminal ```
sudo apt-get update
sudo apt-get install build-essential
``` If it's the latter, type this in ```
sudo apt-get update
sudo apt-get install xmms
``` Oh, and read the second link in my sig.

---

### Post by murrowman789 on 2005-10-22
with that second link, does it apply to '.tar.gz' and such?

---

### Post by aysiu on 2005-10-22
[QUOTE=murrowman789]with that second link, does it apply to '.tar.gz' and such?[/QUOTE] I don't think you're understanding how applications install in Ubuntu. Most of the time, you just type a command ```
sudo apt-get install packagename
``` or click a few things in Synaptic (step-by-step tutorial in the second link), and the software is downloaded *and* installed for you. You don't manually download anything. The software is downloaded and installed, and all dependencies are resolved with the click of a few buttons or the typing of a single command. Most of the time--especially for simple applications like XMMS--you don't ever have to download a .deb or a .tar.gz or a .rpm. Please, read the second link the whole way through. The way it installs Blender you can also use as a method to install XMMS.

---

### Post by murrowman789 on 2005-10-22
[QUOTE=aysiu]I don't think you're understanding how applications install in Ubuntu.[/QUOTE]

i think its because i'm so used to slackware. 

i'll figure it out.

---

