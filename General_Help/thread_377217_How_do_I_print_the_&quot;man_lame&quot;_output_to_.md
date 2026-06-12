---
title: "How do I print the &quot;man lame&quot; output to file?"
date: 2007-03-05
forum: General Help
---

### Post by caffienda on 2007-03-05
I am trying to figure out how to use LAME and am trying to print the output of the manual to a text file.  How do I do this? can I use grep?

---

### Post by etank on 2007-03-05
You can do something like this:```
man *somecommand* > file.txt
```
I also was able to find this [http://www.die.net/doc/linux/man/man1/lame.1.html](http://www.die.net/doc/linux/man/man1/lame.1.html). There quite a few places online that have the man pages in html format.

I hope that helps some.

---

### Post by Skidpad on 2007-03-05
> **etank said:**
> You can do something like this:```
man *somecommand* > file.txt
```

Great! Thanks for the tip!

---

### Post by llamakc on 2007-03-05
man yourcommand | lp

or (if you have more than one printer and not one set as default for lpr)

man yourcommand | lp -d "NameOfPrinter"

---

