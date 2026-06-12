---
title: "Boot Problem"
date: 2007-10-19
forum: General Help
---

### Post by exXP on 2007-10-19
When I started with Ubuntu 6.10, I could not get the booting graphic to show.  Booting took about 3 minutes into a blank screen before arriving.  Somebody in this forum kindly suggested that I add 'vga=771' in the menu.lst file. This worked like a charm and ever since, when new menu.lst files have arrived, I have done this successfully.  However, yesterday I up-graded to 7.10 and find that this no longer works.  Once again I'm taking 3-4 minutes to boot up with a blank screen.  Adding 'vga=771' no longer works.  I notice that the hex number following UUID= is different.  I am reluctant to change this without knowing what I am doing.  Does anyone have any ideas?
exXP

---

### Post by strabes on 2007-10-19
Paste the output of these commands inside code tags:```
sudo cat /boot/grub/menu.lst
lspci
```

---

### Post by exXP on 2007-10-19
Thank you for your very rapid response.  Could you enlarge on this for me?  I tried it (accounts for the delay) and got Menu.lst on the screen.
exXP

---

