---
title: "gksudo alternative"
date: 2018-06-04
forum: General Help
---

### Post by rrob3rtt on 2018-06-04
How can I run a graphical application as root on ubuntu 18.04?

---

### Post by Morbius1 on 2018-06-04
Let's say I wanted to edit fstab as an example:
```
gedit admin:///etc/fstab
```
To bring up nautilus:
```
nautilus admin://
```

[COLOR=#0000cd]*You can also consider going to the future of the Linux desktop and use Xubuntu instead. In Xubuntu the command would look somewhat familiar - just replace gksudo with pkexec:*[/COLOR]
```
pkexec mousepad /etc/fstab
```
```
pkexec thunar
```

---

