---
title: "Searching for Text Within File"
date: 2007-04-05
forum: General Help
---

### Post by snowdonkey on 2007-04-05
Greetings,

I have a bunch of Java source files inside a directory.  I'd like to get a list of each file that contains the text "examine".

Is searching this way possible without opening each file individually?

Thanks!

---

### Post by irwa82 on 2007-04-05
hi,

I am personally a command line man and would do the following.

$ grep -i examine *    (does all files in that directory case insensitive)
$ grep -ir examine *   (does all files in that directory and goes recursively into other directories)
$ man grep          (full description of grep)

---

### Post by girishv on 2007-04-05
Hi,

irwa has answered your question. The flags he has given prints the lines containing the word too. If you want just the file names to be listed, you can use the flag -l

grep -irl examine *

Girish

---

### Post by snowdonkey on 2007-04-05
Thanks to you both, grep -ir examine * was perfect!

---

