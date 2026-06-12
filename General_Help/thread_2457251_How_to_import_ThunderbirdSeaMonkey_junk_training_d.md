---
title: "How to import Thunderbird/SeaMonkey junk training data into Bogofilter?"
date: 2021-01-28
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-01-28
Title says it all

* Update: In case it's relevant, turns out the specific Bogofilter I would like to import into is the one bundled with the flatpak of Evolution.

---

### Post by &amp;KyT$0P# on 2021-01-30
bump

---

### Post by &amp;KyT$0P# on 2021-01-31
I found this Java program called Bayes Junk Tool -
```
https://ftp.osuosl.org/pub/mozdev/bayesjunktool/bayesjunktool-0.2.1.jar
```
Which although old seems to run on Xubuntu 20.04 and seems able to read my training.dat. (I also have a [FONT=Courier New]traits.dat[/FONT] file, which it can't read.  But that file is only 8 bytes, while my training.dat is almost 500 KB, so probably I can ignore traits.dat for this purpose?)

This program looks to be able to export the training data in a few different formats.  If there's no direct way to get my training data into Bogofilter, can I import/convert an export from this progam into Bogofilter?

---

### Post by &amp;KyT$0P# on 2021-02-02
Think I've figured it out.  My searching for "bogofilter" was throwing me off.  The command I need is actually [FONT=Courier New]bogoutil -l [/FONT].

I don't think it's technically possible to do a "perfect" import.  There are too many differences in Thunderbird tokens vs Bogofilter tokens.  But combining Bayes Junk Tool and bogoutil still seems better than starting from scratch and is probably the best I can do.

---

