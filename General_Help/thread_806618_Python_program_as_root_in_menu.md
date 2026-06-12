---
title: "Python program as root in menu"
date: 2008-05-25
forum: General Help
---

### Post by gaiterin on 2008-05-25
Hi!
I did a program in Python + Glade, and I need to be run as root.
I did "Allow executing as program".

To run, in console:
```
sudo Python program.py
```

To do that from Nautilus:
```
gksudo Nautilus
```
Then double click on the file program.py


But ... **How I do it from the menu Gnome?**
Putting:
```
gksudo python /path/program.py
sudo python /path/program.py
gksudo /path/program.py
sudo /path/program.py
```
or the same options with flag "Terminal".

**It does not work!**

Thank you!

---

### Post by jrib on 2008-05-25
Elaborate on "does not work".  Does it open at all?  Do you get errors?  Anything in ~/.xsession-errors?

---

### Post by gaiterin on 2008-05-26
Thanks.
It was the path of glade file.
It didn't find.
I use the fuctions of know path.
Regards.

---

