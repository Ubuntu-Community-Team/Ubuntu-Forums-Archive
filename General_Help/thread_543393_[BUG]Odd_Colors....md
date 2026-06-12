---
title: "[BUG]Odd Colors..."
date: 2007-09-05
forum: General Help
---

### Post by Shoot3r101 on 2007-09-05
Well when ever I open an application I get a few lines of odd colors for a split second then goes away. I did however manage to get a screen shot of these odd colors [clicky clicky!]("http://i197.photobucket.com/albums/aa37/Shoot3r101/Screenshot.png")

---

### Post by eggdeng on 2007-09-05
Check out the make of your graphics card ```
lspci | grep VGA
``` and that you are using an appropriate driver ```
cat /etc/X11/xorg.conf | grep Driver
```

---

