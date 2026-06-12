---
title: "menu entry for ./ executable"
date: 2013-05-29
forum: General Help
---

### Post by frogotronic on 2013-05-29
Hi,

  I'd like to create a menu entry for a program that I normally start via the terminal (in the run directory) by typing <./start>

  What would the menu entry look like?  sh /"<path_to_directory>/start" ?

Thanks,
CH

---

### Post by ohnonot on 2013-05-29
what menu?
generally you can just start it like any other program (without 'sh') and yes, with the full path.
unless you need to see the programs output in a terminal window.

---

### Post by HiImTye on 2013-05-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
the entry '.' is a special folder that means 'this folder' so if you tried the command elsewhere you would need to add the path or a variable equal to it's path, such as
```
$HOME/path/to/file
$PWD/path/to/file
~/path/to/file
```
etc. the exceptions are those in your $PATH variable

---

