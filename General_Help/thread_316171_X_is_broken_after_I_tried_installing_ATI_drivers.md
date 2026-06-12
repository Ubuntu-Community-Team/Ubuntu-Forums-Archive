---
title: "X is broken after I tried installing ATI drivers"
date: 2006-12-10
forum: General Help
---

### Post by jincast90 on 2006-12-10
So I have actually used Ubuntu for some months, but I havent really cared about 3d accelaration undtil recently. So I tried to install the ATI drivers, but after I rebooted I got an error saying that X didint work, so now I am stuck without a GUI. How can I recover my GUI?

---

### Post by chalex on 2006-12-10
you will need to edit your /etc/X11/xorg.conf file.  Did you make a backup copy before you changed it?

1)Hit Ctrl+Alt+F1 to switch to a console
2) log in
3) sudo pico /etc/X11/xorg.conf
4) change the Driver section to say "ati" instead of "fglrx".

Of course, you don't have to use pico, you can use your favorite editor.  You may also need to make more changes to the config file, depending on what you changed before.

---

### Post by wombat20 on 2006-12-10
Run this at the command line and if nothing else works select VESA.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jincast90 on 2006-12-12
I just reinstalled.. Damn why is 3d acceleration so damn hard to get working in Ubuntu :(

---

