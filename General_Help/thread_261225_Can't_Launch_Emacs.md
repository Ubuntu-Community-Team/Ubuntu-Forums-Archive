---
title: "Can't Launch Emacs"
date: 2006-09-19
forum: General Help
---

### Post by jslmsca on 2006-09-19
I unsuccessfully tried to install a better looking version of Emacs based on a 'How to' I found searching the forums.  I then used Synaptic Package Manager to uninstall all traces of Emacs, following by using Add/Remove to install the generic version.  Now, Emacs 21 (X11) is listed under Programming but clicking on it does nothing.  In the terminal, typing 'sudo emacs' produces the following: Undefined color: "black".

emacs
emacs21
emacs21-x
emacsclient
emacsclient.emacs21

are listed in /usr/bin

emacs
emacs21

are listed in /usr/share

Any help would be appreciated.  Thanks.

---

### Post by croak77 on 2006-09-20
Are you using Xgl?

---

### Post by jslmsca on 2006-09-20
Yes.  Would that make a difference?

---

### Post by jslmsca on 2006-09-20
I found the solution in the archives:
[http://www.ubuntuforums.org/archive/index.php/t-90751.html](http://www.ubuntuforums.org/archive/index.php/t-90751.html)

Somehow, emacs couldn't find the rgb.txt file which contains the color definitions.  Symbolic links seems to fix it.

---

