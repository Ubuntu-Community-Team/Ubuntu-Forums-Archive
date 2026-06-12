---
title: "root/home folder"
date: 2014-09-18
forum: General Help
---

### Post by lumaja2 on 2014-09-18
Ubuntu 12.04
  Add by mistake a directory and files [/SIZE][SIZE=3]into root/home folder how to remove them.
Thank you

---

### Post by Bucky Ball on 2014-09-18
If you are using Nautilus file manager, for instance, you could try:

```
gksudo nautilus
```

Navigate to /root/home and remove the files. Close the file manager window immediately, don't hang about as you are logged on to it as root and you can cause serious damage fooling around. Replace 'nautilus' in the command above with the name of your chosen file manager.

PS: Please use default font and pt size. ;)

---

