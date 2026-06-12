---
title: "emulating gnome-terminal backspace settings in xterm"
date: 2006-07-02
forum: General Help
---

### Post by b7j0c on 2006-07-02
gnome-terminal has a nice dialog in the profile editor to use control-H as the delete key, which is useful for me when i am connecting to a freebsd server at work from my ubuntu laptop and then running gnu screen

does anyone know who to do this with a plain xterm? i don't know how to set TERM values etc, and i haven't had luck just doing stty erase ^H on the target box.

thanks!

---

### Post by x1a4 on 2007-02-26
Hi,

You can configure XTerm in ~/.Xdefaults

Syntax is: 

App.Resource: value

For example: 

XTerm.backarrowKeyIsErase: True   

should set XTerm's backspace key to erase.  

For more XTerm resource names see the XTerm man page: *man xterm*, or if you prefer the GUI use *yelp*

---

