---
title: "Im in trouble with xserver"
date: 2008-05-24
forum: General Help
---

### Post by jrharvey on 2008-05-24
So i recently let my laptop die when the battery ran dead and when i restarted for some weird reason it broke my xserver file. So now X doesnt start and i tried the whole ```
sudo dpkg-reconfigure xserver-xorg
``` but it is not letting me do anything. The keyboard is not working at all once i start to reconfigure X. This is sooooooooo weird. Need some help here.

---

### Post by Thanoulis on 2008-05-25
From a terminal (Alt+Ctrl+F<1-6>), log in and type:
```
sudo rm /tmp/.X0-lock
```
Then restart your X server, or reboot...

Or, if you still have trouble with the keyboard, enter single-user mode from the Grub menu (i think it's called recovery)
and do the same.

---

### Post by jrharvey on 2008-05-26
didnt do anything, the keyboard is still locked. In gutsy when the xserver broke it took you to a nice GUI that let you choose which driver you wanted to use. What happened to that????? It was nice to have and did they ditch that idea???

and when i tried to do that command it only told me there was no such file.

---

### Post by jrharvey on 2008-05-27
is there a way to set the xserver to its default????? Im at a loss as to what to do here guys.

---

### Post by jrharvey on 2008-05-27
bump

---

