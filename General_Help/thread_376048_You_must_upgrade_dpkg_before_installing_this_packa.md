---
title: "You must upgrade dpkg before installing this package??????"
date: 2007-03-04
forum: General Help
---

### Post by dustin0 on 2007-03-04
I played with some stuff (ill never do it again :P) and somehow if messed with dpkg so i get this error

"You must upgrade dpkg before installing this package."

Soooo is there a command to upgrade dpkg??

 - Dustin

---

### Post by dustin0 on 2007-03-04
bump

---

### Post by troymcdavis on 2007-04-03
Give us the output of ```
$ sudo aptitude show dpkg
``` if you could.

You might want to try ```
$ sudo aptitude update && sudo aptitude upgrade
``` and seeing if that's the problem (you can go ahead and do that). You might have to try ```
$ sudo aptitude reinstall dpkg
```. The output of "aptitude show" might give us some hints if both of those don't work.

---

