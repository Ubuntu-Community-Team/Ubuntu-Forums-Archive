---
title: "usplash not displayed"
date: 2008-03-31
forum: General Help
---

### Post by callkalpa on 2008-03-31
I'm using Ubuntu 7.10. When I start my computer I get the Grub menu and when I select to boot Ubuntu, the screen displays a message "frequency out of range". Hioe something is wrong with my monitor ....

But after a few minutes the ubuntu log in window appeares. The thing as I think is that the usplash screen is not displayed it the boot process.

How can I fix this issue ?

Thank you.

---

### Post by jakupl on 2008-03-31
This is a wild guess, but you could try to write:
```
$ sudo gedit /etc/usplash.conf
```

and change it from 1280 x 1024 to 1024x768... reboot and see what happens?

---

### Post by jakupl on 2008-03-31
and while your at it, do the
```
$ sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by callkalpa on 2008-03-31
It worked.
Thank you very much.

---

