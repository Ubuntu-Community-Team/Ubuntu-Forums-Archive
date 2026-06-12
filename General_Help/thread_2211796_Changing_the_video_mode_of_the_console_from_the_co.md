---
title: "Changing the video mode of the console from the console"
date: 2014-03-17
forum: General Help
---

### Post by pwabrahams on 2014-03-17
There's lots of information around on how to change the video mode by changing the grub configuration.  But that doesn't apply when you're running the installation DVD.  I want to change the console video mode from the console itself by using the command line.  I assume that it's some variation of the **set** command.  How can I do that? (The font is too small to be easily readable.)

---

### Post by SeijiSensei on 2014-03-18
Do you have an NVIDIA adapter perhaps?  I've always had a problem with the font being miniscule on machines with an NVIDIA adapter until I create an xorg.conf and add the "DPI" option as described [here](http://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards).

---

### Post by pwabrahams on 2014-03-18
I don't believe that xorg.conf affects the font used in virtual consoles.   There's a way to set it in the grub configuration, but I want to do it on the fly -- from the virtual console itself.  Some kind of set command, I presume -- but what? To clarify further, I'm looking for a command-line equivalent of the grub command **vga=**.

---

### Post by SeijiSensei on 2014-03-19
I browsed around a bit searching for an answer to your question.  It doesn't appear possible outside of grub.  I found [this discussion at Arch](https://bbs.archlinux.org/viewtopic.php?id=46592) informative.

---

