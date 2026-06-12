---
title: "System Failure"
date: 2006-12-19
forum: General Help
---

### Post by golf22r on 2006-12-19
Hi, I recently tried to install XGL/Compiz from the directions found at [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)  and now when I start Ubuntu it just goes to a blank screen.  Is there any way I can restore Ubuntu?  I am using Ubuntu 6.10 on an Hp Pavilion laptop with a Nvidia graphics card.  Thank you.

---

### Post by taurus on 2006-12-19
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

