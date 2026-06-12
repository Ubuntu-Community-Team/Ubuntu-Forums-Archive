---
title: "Please help: compilation error : aspell ??"
date: 2007-04-01
forum: General Help
---

### Post by eljalill on 2007-04-01
Hello!

I am trying to compile amyedit, because I need to use texlive and my favourite LaTex editor (winefish), can't do without tetex. So, I found amyedit, and it seems the most like it.

I've downloaded the sourcecode from sourceforge.net, and after installing a few libraries, ./configure exits without errors or warnings.

However, make just doesn't work and I get this error:
```

In file included from AmyEdit.hh:31,
                 from AboutDialog.cc:51:
EditTabs.hh:30:20: error: aspell.h: No such file or directory
make[2]: *** [AboutDialog.o] Error 1
make[2]: Leaving directory `/home/eljalill/Desktop/amyedit-1.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/eljalill/Desktop/amyedit-1.0/src'
make: *** [all-recursive] Error 1

``` .

I even tried it with amyedit 0.9, 0.8 und 0.7, but always the same problem, and I checked, but my aspell is the newest version (in case that has anything to do with it).

Please, does someone know how to do this? 
eljalill

Edit: Resolved... had to install libaspel-dev ...
Although i have no clue, why it's not listed in the dependencies, and configure doesn't complain, when I don't have it...

---

### Post by djrosen on 2007-04-01
if you dont want spell checking built in check the configure options for something like --without-aspell, if that is not an available configure option you will need to install the development libraries for aspell.

$ sudo apt-get install libaspell-dev

then redo ./configure

EDIT: You will probably want to do a "make clean" also.

---

### Post by eljalill on 2007-04-03
Thanks! I had been wondering, what this aspell is for.... 
Installed it correctly now. :)

---

