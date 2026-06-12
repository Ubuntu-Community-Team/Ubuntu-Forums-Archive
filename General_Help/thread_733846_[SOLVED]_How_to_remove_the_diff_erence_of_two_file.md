---
title: "[SOLVED] How to remove the diff erence of two files?"
date: 2008-03-24
forum: General Help
---

### Post by davidpbrown on 2008-03-24
I'm thinking this maybe a daft question but I have a headcold and can't think straight so here goes..

How can I get the similarity of two files - not the difference?
For instance, if I have two package lists how do I resolve the similarity?

I've tried reverse patching the diff with no apparent success and a load of errors. That was my first attempt using diff so I don't know if that's the way forward..

:confused:

---

### Post by Nameless_one on 2008-03-24
Try this: 

[http://catb.org/~esr/comparator/](http://catb.org/~esr/comparator/)

Plus there seems to be another program, comm:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?comm](http://unixhelp.ed.ac.uk/CGI/man-cgi?comm)

Both from Google.

---

### Post by Athelstan101 on 2008-03-24
This will print out the duplicated lines:
```
$ sort file1 file2 | uniq -d
```

---

### Post by davidpbrown on 2008-03-24
Many thanks..

comm -1 -2 file1 file2 > output

seems to have worked well.

:)

---

### Post by davidpbrown on 2008-03-24
and 
sort file1 file2 | uniq -d

works too..

Thanks for the quick reply !

---

