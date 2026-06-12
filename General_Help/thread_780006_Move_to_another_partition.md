---
title: "Move to another partition?"
date: 2008-05-03
forum: General Help
---

### Post by K.Morgan on 2008-05-03
Hi, i would like to create a backup of my home folder in ubuntu 8.04 to a new partition i have created, but when i go to move the folder to the new partition i get permission denied.  How do i get around this?

Kristian

---

### Post by Zorael on 2008-05-03
Try doing it with superuser permissions. To launch Nautilus (the Gnome file manager), open a run box with Alt+F2 and enter '**gksu nautilus**'.

Once moved, your files *shouldn't* be owned by root; it should preserve ownership.

IF it somehow managed to make them owned by root, you need to transfer ownership to yourself. I'm not sure this can be done in Nautilus by right-clicking the folder, but it seems to me it should be possible. Make sure to change both user ownership and group ownership.


The terminal way would be this. You need basic shell knowledge for this.
```
$ sudo chown *<your username> <your user directory> -R*
$ sudo chgrp *<your user group> <your user directory>* -R
```
Your group name is by default the same as your username, but to make sure, enter this in a terminal. It'll output all available groups, and yours is usually the first in the list.
```
$ groups
```



As an example, my login is **zorael** and my group is **sunspire**. For the sake of the argument, I'm assuming I mounted my new home folder in **/media/newhome**. As such, the terminal commands for me would be these.
```
$ cd /media/newhome
$ sudo chown zorael /media/newhome/zorael -R
$ sudo chown sunspire /media/newhome/zorael -R
```

---

### Post by K.Morgan on 2008-05-03
Thanks, but when i try to move the folder even after using gksu nautilus i get:

Error while copying.

Files in the folder "kristian" cannot be handled because you do not have permissions to see them.


Kristian

---

### Post by Zorael on 2008-05-03
Terminal way:
[code]$ sudo cp ~ /media/newhome/*<username>* -R
$ sudo chown *<username>* /media/newhome/*<username>* -R
$ sudo chgrp *<user group>* /media/newhome/*<username>* -R

---

