---
title: "[SOLVED] how can i set default xterm size?"
date: 2008-03-25
forum: General Help
---

### Post by fela on 2008-03-25
well the title says it all. I am looking for a command line option for starting up xterm (note: xterm NOT gnome-terminal or konsole) using a specified size for the terminal window, as the default xterm size is way too small. nb. i would like to keep the font size the same, but the window bigger, not both bigger.

thanks for any help

---

### Post by lloyd_b on 2008-03-25
> **fela said:**
> well the title says it all. I am looking for a command line option for starting up xterm (note: xterm NOT gnome-terminal or konsole) using a specified size for the terminal window, as the default xterm size is way too small. nb. i would like to keep the font size the same, but the window bigger, not both bigger.

thanks for any help

"xterm -geometry 132x40"  will start xterm with 132 character width, and 40 character height.  Vary the numbers to taste...

Lloyd B.

---

### Post by x1a4 on 2008-03-25
Another way is to add the following to ~/.Xdefaults
```
XTerm*geometry: *<width>*x*<height>*
```
Optionally you can also specify the position:
```
XTerm*geometry: *<width>*x*<height>*+*<left>*+*<top>*
```

This way all xterms will be opened with the specified geometry, unless overriden in the command.

---

### Post by fela on 2008-03-26
thanks for the replies, esp. the last one, i might try that.

Btw, i did --geometry and didn't even try -geometry (only one -)!!! omg what a waste of time :lolflag: oh well seems to be solved now doesn't it...

---

