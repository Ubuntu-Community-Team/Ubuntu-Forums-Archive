---
title: "Grub.conf empty?"
date: 2007-02-25
forum: General Help
---

### Post by chickensofdoom on 2007-02-25
Since my family has started complaining about GRUB and accidentally booting into Ubuntu, I decided to look into changing the default selection for the timeout. I followed the directions I found, but when I open up my grub.conf file, I find that it's empty. I just putting default=4 and saving, but that had no effect.

What's going on?

---

### Post by rsambuca on 2007-02-25
Actually, the file that you want to edit is:```
/boot/grub/menu.lst
```

I also changed the "timeout" line in my menu.lst to 2 seconds.  That way when my wife boots up the machine, it goes straight into XP with little delay, and I just have to press an arrow key at the right time.  Eventually, she will learn to love linux!

---

### Post by po0f on 2007-02-25
chickensofdoom,

Edit /boot/grub/menu.lst instead.

---

