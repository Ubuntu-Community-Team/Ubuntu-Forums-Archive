---
title: "Unable to mount partition in Ubuntu 12.10"
date: 2013-03-15
forum: General Help
---

### Post by ez elarab on 2013-03-15
I have ubuntu beside win xp
I have chekdsk into xp and while booting also
I cant open any partation .. this is the photo

[http://im32.gulfup.com/6E5OY.png](http://im32.gulfup.com/6E5OY.png)
[[img]http://im32.gulfup.com/6E5OY.png[/img]](http://www.gulfup.com/?0ZQ2Tb)

---

### Post by ez elarab on 2013-03-15
while searching i found the solve
type the next into terminal

sudo mkdir /media/$USER
sudo chown $USER.$USER /media/$USER

thanks

---

