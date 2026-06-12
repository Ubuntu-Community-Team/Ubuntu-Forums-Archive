---
title: "Grup boot list save"
date: 2008-01-23
forum: General Help
---

### Post by BuddhaDave on 2008-01-23
Help. I am a Ubuntu newbie I edited my grub boot list to make my Vista the default but I cant save the file . Can someone give me the command line?

---

### Post by y-lee on 2008-01-23
You need to be a superuser to edit and save the menu.lst file.

try  ```
sudo gedit /boot/grub/menu.lst
```
in the terminal to edit and save this file.

Back it up first tho might be a good idea :)

---

