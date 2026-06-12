---
title: "Latex Suite"
date: 2004-11-12
forum: General Help
---

### Post by sickmelon@tiscali.it on 2004-11-12
Hi! I have just downloaded and installed the tetex-bin package from debian site and it completely sucks, i can't get a latex article compile correctly. In synaptic i can only find latex 2.09, there isn't any latex2e. What am i doing wrong?

PS: nevermind the bad english, i'm italian!

---

### Post by WW on 2004-11-12
First, remove whatever it is you installed. (There should be a way to uninstall it.)

Ubuntu has tex/latex in their repository, so you don't have to get it from the Debian site.  Install these packages: **tetex-base**, **tetex-bin**, and **tetex-extra**.
You can use Synaptic to select and install these, or you can give the following commands:
```
 $ sudo apt-get update
 $ sudo apt-get install tetex-base tetex-bin tetex-extra
```

---

### Post by patrickallo on 2004-11-12
I'm still getting this:

[FONT=Courier New]This is e-TeX, Version 3.1459-2.1 (Web 2C 7.4.5)
ebtering extended mode
(./Bestanden/TeXfiles/abstract.tex
! Undefined control sequence.
l. 1 /documentclass
                              [a4paper,10pt,oneside, dutch]{article}[/FONT]

---

### Post by WW on 2004-11-12
patrickallo:

I'm going to guess that you used the command **tex** on a Latex file.  If so, try again with the command **latex**.

---

### Post by patrickallo on 2004-11-12
thanks, LaTeX works fine now.

Working from the terminal is still a bit odd when used to TeXshop on OS X

---

### Post by drunken-wallaby on 2004-11-12
[QUOTE=patrickallo]Working from the terminal is still a bit odd when used to TeXshop on OS X[/QUOTE]
Hi there. If you don't mind installing some KDE packages, you might be fine with kile, which is a text-editor with some built in tex-functions :) ```
sudo apt-get install kile
``` there are some java-based editors around as well. and of course emacs and vim ```
sudo apt-get install vim-latexsuite
``` hope that helps :)

---

### Post by sickmelon@tiscali.it on 2004-11-13
Dammit i forgot tetex-extra! ](*,) 

Messing around i found Texmacs, and it seems pretty smart and useful for my simple university relations/articles. But it's also pretty buggy and the non-GTK interface sucks...

---

