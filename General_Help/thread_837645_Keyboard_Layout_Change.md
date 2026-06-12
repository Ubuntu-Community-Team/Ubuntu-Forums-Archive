---
title: "Keyboard Layout Change"
date: 2008-06-22
forum: General Help
---

### Post by Houli on 2008-06-22
Hi, I was wondering how to change my keyboard layout. For some strange reason my at key is now the double quotes and some other things have changed as well.

---

### Post by Christmas on 2008-06-22
Try [this](http://www.howtoforge.com/changing-language-and-keyboard-layout-on-various-linux-distributions) guide.

Open your terminal and type:
```
sudo dpkg-reconfigure console-setup
```
Or *dpkg-reconfigure console-data*, one of them should work.

---

