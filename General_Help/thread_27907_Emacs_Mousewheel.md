---
title: "Emacs Mousewheel"
date: 2005-04-18
forum: General Help
---

### Post by thinusp on 2005-04-18
Hi there

I'm using emacs under X and was wondering how to get the mousewheel to scroll the document. It used to work in suse, but not in ubuntu.

Thanx
Thinus

---

### Post by Leif on 2005-04-18
Add this to your ~/.emacs file (create it if it doesn't exist) :

(mouse-wheel-mode)

You also might want to add these, as having the beep everytime you scroll to the top/bottom of a document gets old pretty quickly :

(setq bell-volume 0)
(setq sound-alist nil)

---

### Post by thinusp on 2005-04-20
Thanx!! Works perfectly now. I only recently started using emacs, great editor for writing code and tex documents

Cheers
T

---

