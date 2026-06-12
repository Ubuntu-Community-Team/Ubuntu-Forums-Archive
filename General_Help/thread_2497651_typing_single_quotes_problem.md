---
title: "typing single quotes problem"
date: 2024-05-13
forum: General Help
---

### Post by ginost7 on 2024-05-13
hello 

cannot type single quotes on my keyboard, Can anybody help?

Gino 				

(base) gino@gino-Precision-7770:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.2 LTS"
(base) gino@gino-Precision-7770:~$

---

### Post by #&amp;thj^% on 2024-05-13
Have you looked in " Preferences -> Keyboard -> Other Options... -" is it set correctly?
Also show us this:

```
less /etc/default/keyboard


# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
BACKSPACE="guess"

```

---

