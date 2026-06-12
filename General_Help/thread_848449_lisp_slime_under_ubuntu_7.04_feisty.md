---
title: "lisp slime under ubuntu 7.04 feisty"
date: 2008-07-03
forum: General Help
---

### Post by steveeq1 on 2008-07-03
I did:
sudo apt-get install clisp
sudo apt-get install slime

When I go into emacs and type "alt-x slime", I get the following error:
[1]>
*** - LOAD: A file with name
      /usr/share/emacs/site-lisp/slime/swank-loader.lisp does not exist
The following restarts are available:
ABORT          :R1      ABORT


I have looked all over the internet and couldn't find the solution to this problem. I tried another 7.04 machine and had the same problem. I tried altering my .emacs file as follows:
(setq inferior-lisp-program "/usr/bin/clisp")
(add-to-list 'load-path "/usr/share/emacs/site-lisp/slime")
(require 'slime)
(slime-setup)

Still the same problem. Anyone know the answer?

---

