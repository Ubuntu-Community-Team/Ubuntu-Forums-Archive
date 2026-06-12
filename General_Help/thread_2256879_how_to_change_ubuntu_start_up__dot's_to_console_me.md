---
title: "how to change ubuntu start up  dot's to console messages?"
date: 2014-12-15
forum: General Help
---

### Post by shamsat on 2014-12-15
When i boot ubuntu 14.10, it some time hangs, i want to change the ubuntu boot do'ts to boot up console messages to know where is the problem, how i can do it?

---

### Post by nerdtron on 2014-12-15
Have you tried pressing the up/down arrow keys when ubuntu start to load?

---

### Post by CantankRus on 2014-12-15
Edit **/etc/default/grub** and for the line.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Change to ...
```
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```
Update grub...
```
sudo update-grub 
```

---

