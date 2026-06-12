---
title: "lightdm blackscreen When use systemd boot affter Install Ubuntustudio on Ubuntu 15.4"
date: 2015-04-25
forum: General Help
---

### Post by Bymyself9696 on 2015-04-25
I must use Kennel with old upstart boot option to boot Without lightdm black screen Or otherwise change display manager like gdm or sddm :-|

---

### Post by kc1di on 2015-04-25
Hello Bymyself9696 and welcome to Ubuntu Forums,

Usually blank screen is the result of wrong video driver for your card.  Do you know the video card you have installed if not and you can get to a terminal type the following command and post output here. (note you can just copy and past them in the terminal)

```
lspci | grep VGA i
```

Also ```
lsmod
```

That should give us a start.

---

