---
title: "Login problem"
date: 2008-06-22
forum: General Help
---

### Post by Kiryu on 2008-06-22
:confused:  I changed the GDM theme on a wubi Ubuntu 8.04 ( FULLY UP TO DATE ) install , and now I can't login...  I get an error message (GDM GREETER CRASH) ( going to post here later ) . I know I just need to Change the GDM login theme ... How can I do this  ( back to default) from the terminal?! 

Please help me!

I'm from brasil , so my english is not the best.

---

### Post by macaholic on 2008-06-22
To change the GDM preferences get into a tty terminal (Ctrl + Alt + F1) type ```
sudo nano /etc/gdm/gdm.conf
```Search for the part that lists GtkTheme, and cahnge it back to Human.

---

