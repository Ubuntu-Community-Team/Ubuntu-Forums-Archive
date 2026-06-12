---
title: "emacs and csharp-mode.el font color not working"
date: 2005-07-25
forum: General Help
---

### Post by flip on 2005-07-25
I'm trying to get csharp-mode.el (C#) installed and the font coloring isn't working. My machine at work (Fedora Core 3) doesn't seem to have any problems, just drop the el file into /usr/share/emacs/site-lisp/ and presto. The default emacs with Ubuntu seems to be having troubles. 

Any help on even where I should start looking for a fix would be great (aside from reading through all the emacs docs on the gnu web site ... gah!)

Cheers

- flip

---

### Post by flip on 2005-07-28
Turns out this was a pretty easy fix. Figured out it wasn't a problem with csharp-mode.el when I dug out some of my old c code (oh how I miss c). Turns out cc-mode didn't have any colors either!?

Problem is in emacs config. The emacs21 deb for Ubuntu comes with Global-Font-Lock off? Strange. It's under the Options tab, first choice at the top. Easy enough fix for me (still an emacs newb).

This seems kinda strange to me though, figure that would be on by default. No harm no foul though, just something for all the other newbs to look out for.

- flip

---

