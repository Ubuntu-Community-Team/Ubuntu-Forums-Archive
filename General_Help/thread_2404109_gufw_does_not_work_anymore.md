---
title: "gufw does not work anymore"
date: 2018-10-20
forum: General Help
---

### Post by ofbodhqwodufb on 2018-10-20
Hello,

I use gufw under Ubuntu 18.04 and it does not run anymore after entering my administrator password.

I get this this:```
ec4g@ec4g-MS-7996:~$ sudo gufw
Traceback (most recent call last):
  File "/usr/share/gufw/gufw/gufw.py", line 21, in <module>
    from gufw.view.gufw  import Gufw
  File "/usr/share/gufw/gufw/gufw/view/gufw.py", line 18, in <module>
    import gi
ModuleNotFoundError: No module named 'gi'
```

Thank you for your help

---

### Post by dino99 on 2018-10-20
Maybe you are logged on a 'wayland' session; try a xorg one.

---

### Post by ofbodhqwodufb on 2018-10-20
Hello, it does not work either. In fact, it follows the installation of python

---

