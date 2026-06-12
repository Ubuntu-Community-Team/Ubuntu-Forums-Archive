---
title: "Custom Kernel Compilation that only compiles parts currently used? Tips on compiling"
date: 2014-06-04
forum: General Help
---

### Post by jewfromdahood2 on 2014-06-04
It's been a while since compiling my own kernel, I remember there  being some way to only select all the parts of the Linux kernel in  compilation in one of the steps, how do I go about doing it? I'm trying  to shake off the rust I have from not playing with Linux so much and  wanted to make a custom kernel to help familiarize myself in some  different ways. Does anyone know what I am talking about? I'm using  14.04 64 bit if that helps. I just don't want to have to spend a long  time unchecking a majority of the drivers, modules, and other stuff.   While we are at it, what are some tweaks and settings to the Ubuntu  kernel to help out a Intel Core i3 Home theater PC using Intel  integrated graphics. I want to get as much oomph out of it as possible.

---

### Post by Doug S on 2014-06-05
Hi and welcome to Ubuntu forums.

Are you thinking of this:> Since the 2.6.32 kernel, a new feature allows you to  update the configuration to only compile modules that are actually used  in your system: 

make localmodconfigwhich I got from [here]("https://help.ubuntu.com/community/Kernel/Compile") (I don't use it myself, but I do compile the kernel "the old-fashioned Debian way").

---

### Post by jewfromdahood2 on 2014-06-05
YES!!!! That's the one I was thinking of! I needed it to slim down the HTPC kernel I have as it's pretty much never going to have new hardware

---

