---
title: "How to check a file"
date: 2013-02-05
forum: General Help
---

### Post by dlw1146 on 2013-02-05
I need to open a file to look for a problem.
The file is 'fastboot.linux' which has a purple square for an icon.

Can this be done and if so how?

dlw

---

### Post by Cheesemill on 2013-02-05
What type of file is it?

If it is a text file then you can open it with gedit. If it is a binary file then you either have to open it with a program that understands the format or try looking at the raw data with a hexeditor (this will probably be unintelligible though).

You can find out what type of file it is using the 'file' command...
```
file fastboot.linux
```

---

