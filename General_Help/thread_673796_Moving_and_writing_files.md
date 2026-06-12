---
title: "Moving and writing files"
date: 2008-01-21
forum: General Help
---

### Post by werg on 2008-01-21
I'm relatively new to Ubuntu and Linux altogether. I was trying to install some programs but they require me to write into directories that I apparently don't have permission to alter. I understand that I need a root clearance level, and that Ubuntu rather relies on Sudo for this purpose. What are the steps I should take so that I'm allowed to write and erase within those said directories?

Thank you

---

### Post by z0mbie on 2008-01-21
You can launch *nautilu*s, the file manager with root privilege by pressing ** ALT+F2** and type the command:```
 gksudo nautilus
```

---

### Post by banewman on 2008-01-21
The idea behind sudo is that you only have admin rights for that command and only if your user has admin rights.
in a terminal - sudo <command> - then gives a prompt for your password (your login password) and if you have admin rights then the command is performed.
sudo make install - is an example for installing programs to directories that are owned by root
:)

---

### Post by werg on 2008-01-21
Okay, thank you very much. Another question; say I want a software to have full access rights (writing, deleting) over a directory, how do I instruct this?

Thanks

---

