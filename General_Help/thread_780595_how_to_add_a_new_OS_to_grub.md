---
title: "how to add a new OS to grub"
date: 2008-05-03
forum: General Help
---

### Post by Helios38 on 2008-05-03
Ello,


I am wanting to install possibly puppy to my computer, i am planning to put it on a secondary IDE drive with its own partition.


how would i go about adding puppy to grub?


any help, tutorials, links, anything would be appreciated.

---

### Post by damis648 on 2008-05-03
goto terminal and
```
sudo gedit /boot/grub/menu.lst
```
then scroll to the bottom and add the entry

---

### Post by Helios38 on 2008-05-03
hmm. i'll try this and post the results.

---

### Post by Helios38 on 2008-05-03
it worked, thanks!

---

