---
title: "emacs error"
date: 2007-02-25
forum: General Help
---

### Post by Dearhell on 2007-02-25
When I start the emacs through aplications -> programming -> emacs I get this error in the emacs window:

> 
An error has ocurred while loading '/home/laptop/.emacs'

File error: "Cannot open load file", "tex-site"


But if I start it from the console as root, it works fine

Is there anyway to fix this?

Is there anyway to execute automatically the emacs in the programming tab as root?

---

### Post by nereid on 2007-02-26
Why would you want to start emacs as root?

```

gksudo emacs

```

This seems to me like a non existing package which should be loaded from your .emacs file. Are you sure that you've got the tex-site package installed?

---

### Post by Dearhell on 2007-02-26
> **nereid said:**
> Why would you want to start emacs as root?



This seems to me like a non existing package which should be loaded from your .emacs file. Are you sure that you've got the tex-site package installed?

I want to start emacs as root through programming menu, because as root I don't get any errors

```

gksudo emacs

```

Where I have to put this code in order to execute emacs through the programming menu as root (not through the console)?

There is no tex-site package 

I have followed [Emacs & Latex How-to](http://ubuntuforums.org/showthread.php?t=80344&highlight=emacs+latex) that worked fine for me other times before

---

### Post by llamakc on 2007-02-26
What's the permissions of ~/.emacs?

---

### Post by Dearhell on 2007-02-26
Problem fixed

I solve tex-site problem installing auctex

Later I had another problem, it didn't load preview-latex.el, I fixed this editing the line in the .emacs file that I had downloaded from the tutorial (it seems preview-latex.el it's in another directory in Ubuntu now, different from the how-to)

---

### Post by nereid on 2007-02-27
> **Dearhell said:**
> Where I have to put this code in order to execute emacs through the programming menu as root (not through the console)?

Put it everywhere, where you want to start emacs as root (change the menu entry, applet link in the panel and so on).

---

