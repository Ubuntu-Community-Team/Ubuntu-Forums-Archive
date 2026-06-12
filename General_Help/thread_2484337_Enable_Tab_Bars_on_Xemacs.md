---
title: "Enable Tab Bars on Xemacs"
date: 2023-02-23
forum: General Help
---

### Post by bjrosen on 2023-02-23
The Ubuntu version of Xemacs doesn't display the tab bar, the Redhat version does. How do I enable tab bars on the Ubuntu Xemacs? Alternatively how do I compile Xemacs from source on 21.0.4. I've tried compiling 21.5.34 but I'm getting a compile error.

---

### Post by ActionParsnip on 2023-02-23
[https://www.xemacs.org/Releases/index.html#Stable](https://www.xemacs.org/Releases/index.html#Stable)

Xemacs hasn't beenn updated in years.......or am I reading this wrong?

---

### Post by Holger_Gehrke on 2023-02-23
I don't use XEmacs, but in GNU Emacs 27.1 on XUbuntu 22.04 I can use (global-tab-line-mode) in my ~/.emacs ...

Otherwise there's a package elpa-tabbar in the repositories which might give you what you want. It's basically an emacs-lisp package which you would have to (require ) in your ~/.emacs .

Holger

---

### Post by bjrosen on 2023-06-23
There is a new release of Xemacs, 21.5.35, that compiles on Ubuntu. However it looks terrible, there don't seem to be any fonts in the font menu. I configured with the following switches,

./configure --prefix=/usr/local/tools/xemacs_21_5_35 --with-gtk --with-toolbars --with-menubars --with-scrollbars 

That's not sufficient. Are there additional switches that are needed?

---

