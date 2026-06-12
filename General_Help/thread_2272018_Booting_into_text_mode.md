---
title: "Booting into text mode"
date: 2015-04-03
forum: General Help
---

### Post by veddox on 2015-04-03
Hi all,

I would like to add an option to my GRUB boot screen that  will boot up Ubuntu, but without showing the Plymouth boot screen or  launching LightDM/Unity. All it should do is drop me in a tty shell. (Of  course, I would like to keep the standard option - launch with graphics - too.) Unfortunately, I have no clue how to go about that -  any pointers?

Thanks in advance!

---

### Post by sudodus on 2015-04-03
Copy a menuentry in **/boot/grub/grub.cfg** for 'graphical boot'

```
menuentry .... {
...
}
```

to the end of the file **/etc/grub.d/40_custom**

remove **splash** from the linux line, add **text** to that line instead, save the file and run

```
sudo update-grub
```

---

### Post by veddox on 2015-04-04
Great! Thanks a lot, sudodus! I didn't think it would be that easy :-)

Problem solved.

---

### Post by sudodus on 2015-04-04
You are welcome :-)

---

