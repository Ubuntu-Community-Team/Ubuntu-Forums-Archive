---
title: "Need Permission to move files"
date: 2007-06-03
forum: General Help
---

### Post by kdarkentity on 2007-06-03
I need to move files in a folder on my desktop to usr directory in my filesystem

---

### Post by cantormath on 2007-06-03
you can open a terminal and
```
:/$ sudo nautilus
```and nagivate to the files using the gui
or
```
:/$ sudo mv /home/youruser/Desktop/file /usr/ 
```

---

### Post by raja on 2007-06-03
From the terminal, you have to prefix 'sudo' to the copy command. If you prefer doing it from the file browser, use Alt-F2 or the terminal to launch nautilus as root with ```
gksudo nautilus
``` Now you will be able to copy the files.

---

