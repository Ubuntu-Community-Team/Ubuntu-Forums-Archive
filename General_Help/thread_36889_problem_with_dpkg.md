---
title: "problem with dpkg"
date: 2005-05-25
forum: General Help
---

### Post by bendik on 2005-05-25
ive tried to installing the newest ati driver, and followed a article on the forum
[http://www.ubuntuforums.org/showthread.php?t=13226&page=1&pp=10&highlight=installing+latest+ATI+fglrx](http://www.ubuntuforums.org/showthread.php?t=13226&page=1&pp=10&highlight=installing+latest+ATI+fglrx)

but when i try to do the command:

dpkg --force-overwrite -i <driver package name>.deb

i get the error:

dpkg: unknown force/refuse option `owerwrite'

i have the newest version of dpkg, what should i do?

---

### Post by Xian on 2005-05-25
Did you use the sudo command to preface that line?

$ sudo dpkg --force-overwrite -i <driver package name>.deb

---

