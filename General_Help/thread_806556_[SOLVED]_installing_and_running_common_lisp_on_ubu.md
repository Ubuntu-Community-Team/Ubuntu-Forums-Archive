---
title: "[SOLVED] installing and running common lisp on ubuntu"
date: 2008-05-25
forum: General Help
---

### Post by warredsex on 2008-05-25
hi im working on a project that requires common lisp and i have absolutely no idea wat pakages i must install or how to run it.
googling gave me nothing except slime as a result and i didnt understand what it was..can someone help me?

---

### Post by maximinus_uk on 2008-05-25
Short answer: you'll need to install Lisp itself. I suggest Steel Bank Common Lisp. You also need Emacs (really!) and slime, which forms the ideal IDE for Lisp.
So, in a terminal somewhere:

```
sudo apt-get install emacs
sudo apt-get install sbcl
sudo apt-get install slime
emacs

```

When emacs has started, press ALT-x and enter slime and the press return. If all goes well, you are now looking at slimes welcome message.

Of course, now the hard part starts....

---

### Post by warredsex on 2008-05-30
thx! was exactly wat i wanted~!

---

