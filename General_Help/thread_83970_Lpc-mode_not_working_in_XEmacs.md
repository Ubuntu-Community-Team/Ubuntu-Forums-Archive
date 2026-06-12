---
title: "Lpc-mode not working in XEmacs"
date: 2005-10-30
forum: General Help
---

### Post by Jergosh on 2005-10-30
As in title, when I try to load it Emacs says
'Symbol's value as variable is void: c-C++-comment-start-regexp'
Before upgrading from Hoary it also didn't work (and I hoped switching to Breezy would fix it).

xemacs 21.4.17-2ubuntu1
lpc-mode 0.15-1

TIA,
Greg

---

### Post by Jergosh on 2005-11-01
*bump*

---

### Post by fledermaus on 2005-12-28
I suspect XEmacs has gone on to use the new cc-mode which has a different (and better)
mechanism for language support.

Please try [http://users.pepperfish.org/vivek/lpc-mode.0.17beta.el](http://users.pepperfish.org/vivek/lpc-mode.0.17beta.el) 
(you will need to byte compile this file for the mode to work)

If you do not know how to do this, replace /usr/share/emacs/site-lisp/lpc-mode/lpc-mode.el
with this file and do "sudo dpkg-reconfigure lpc-mode"

Note that this new version will /not/ be compatible with emacs21, since that uses 
the old cc-mode, so the dpkg method might not work if you have emacs21 installed.
It works fine with emacs-snapshot though.

---

