---
title: "Can't open file /usr/share/gdm/themes/Human/Human.xml"
date: 2007-08-02
forum: General Help
---

### Post by pininy on 2007-08-02
Hi,

Right after installing Gusty from Feisty, my login screen always points to the old feisty-gdm-theme, anyway of getting rid of the annoying dialog? deleting the or reconfiguring the gdm to point to the file?

many thanks!

Error loanding Human theme
Can't open file /usr/share/gdm/themes/Human/Human.xml

---

### Post by pininy on 2007-08-04
anyone can help?

](*,)

---

### Post by strabes on 2007-08-04
This is a long shot but try ```
sudo dpkg-reconfigure gdm
```

---

### Post by trondhuso on 2008-02-20
Human.xml error is caused by the fact that ubuntu-artwork isn't installed. 

sudo apt-get install ubuntu-artwork

and there you have it.

---

### Post by yuki on 2008-04-29
I had the same problem after installing Fluxbox in a dubious fashion. gdmsetup allowed me to select a theme that was actually present on the system:
```
sudo gdmsetup
```

---

### Post by yuki on 2008-05-17
gdm now displays a slightly random behaviour, loading two or three different screens.

---

### Post by ladjack on 2008-06-10
or just in 8.04
```

sudo apt-get install ubuntu-gdm-themes
```

---

