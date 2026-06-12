---
title: "Strange behaviour while trying to execute a file"
date: 2007-02-28
forum: General Help
---

### Post by sonsnix on 2007-02-28
Hey fellow ubuntu users,

I recently encountered a strange problem. After creating a binary executable with gcc, double-clicking the file on the desktop or in nautilus just worked fine (a gtk window pops up etc.).

Having uploaded and downloaded the file again (on google code), I couldn't execute the file. A message box pops up and says: "No application suitable for automatic installation is available for this kind of file."
Ok, ls -l said, that the file is not executable anymore. So I did a chmod 755, then it was executable, and I actually could execute the file in the terminal, but when I double-clicked the file, the same message box appeared. Now, there are two solutions for this problem (this is reproducable):

1. Renaming the file -> double-click works (even after renaming it back again)
2. Using the properties dialog and clicking "Run file as program" -> what, beside changing the permissions, does this check box do?

ls -l always displays the same, not depending on whether it is possible to double-click-execute the file or not.

Any help would be appreciated!

Thanks in advance!

Greetings,
Markus

If you want to try yourself, here's the link:
[http://cptracer.googlecode.com/files/wxCPTracer-Rev-8](http://cptracer.googlecode.com/files/wxCPTracer-Rev-8)

---

### Post by sonsnix on 2007-02-28
*push*

---

### Post by ~LoKe on 2007-02-28
```
chmod +x file
```
?

---

