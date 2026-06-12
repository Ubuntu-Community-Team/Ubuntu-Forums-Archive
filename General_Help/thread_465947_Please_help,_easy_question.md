---
title: "Please help, easy question"
date: 2007-06-06
forum: General Help
---

### Post by Elena678 on 2007-06-06
I deled a file, it is now in my trash, but i need the file, i tought i had it on my usb, but it isn't, so, how can i take the file back out of the trash, i can see the file, but i can't coppy it :(

Please help me, i realy need it

Greetings

---

### Post by eggdeng on 2007-06-06
Try ```
sudp cp -R /home/username/.Trash/filename /home/username/Desktop
```
Or ```
sudo nautilus
``` to do it in graphic mode.

---

### Post by Shazaam on 2007-06-06
OR, you can open Trash, right-click the file and choose "restore"

---

### Post by Elena678 on 2007-06-06
thx, the seccond was not working, but the first did it, THANKS

---

