---
title: "Messed up my ubuntu GUI, need help"
date: 2008-02-13
forum: General Help
---

### Post by thebum on 2008-02-13
hello, Im a linux newbie. I recently installed ubuntu 7.10.
I just wanted to see if I could run it on my TV through S-Video, so i played around with the display options.  think I might have not set it back to where it was before I started.
Now I can't boot up into the graphical interface (windows), but instead im stuck in text mode (terminal).

how do I fix it from the command prompt??  so i can boot it up like it was, to the ubuntu GUI

thanks

---

### Post by taurus on 2008-02-13
Log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

