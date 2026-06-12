---
title: "Trouble installing shell themes"
date: 2019-12-28
forum: General Help
---

### Post by alvinrr on 2019-12-28
Does my system compatible with Lexis Theme?
I'm using Ubuntu Gnome 18.04 LTS, Gnome 3.28.2
I extracted the file and moved it to .themes, but when I looked at my tweak tools, no Lexis theme.
[https://www.gnome-look.org/p/1012901/](https://www.gnome-look.org/p/1012901/)

---

### Post by Dennis N on 2019-12-28
I tried it in Ubuntu 19.04 and it works. You might try putting the Lexis folder in /usr/share/themes and see if that makes a difference.

---

### Post by alvinrr on 2019-12-28
There was this error.

---

### Post by Dennis N on 2019-12-28
The "Permission Denied" means you need root user permissions (sudo). Use the terminal instead:
Change directory in terminal to ~/.themes (or wherever the theme folder is). Then:
```
sudo cp -R Lexis/ /usr/share/themes
```

---

### Post by alvinrr on 2019-12-30
Thanks, I can use it now.

---

