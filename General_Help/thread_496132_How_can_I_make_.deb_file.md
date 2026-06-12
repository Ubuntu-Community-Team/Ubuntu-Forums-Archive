---
title: "How can I make .deb file"
date: 2007-07-08
forum: General Help
---

### Post by gabeyg on 2007-07-08
How can I make .deb executable form from source code?

---

### Post by Sammi on 2007-07-08
I often use checkinstall, when it's just for my own personal use. You can find it in Synaptic.

Usually when you compile and install from source, you do these three commands:
```
./configure
make
sudo make install
```With checkinstall you do almost the same, just with the last step you use checkinstall to create a deb and install it:
```
./configure
make
sudo checkinstall
```

If you want to create a package for distribution, then you have to go through more. I haven't done it before, but I think you use dpgk for that.

---

### Post by marianom on 2007-07-08
[Here]("http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html") you can find the Ubuntu Packaging Guide. Enjoy!

---

### Post by Sammi on 2007-07-09
> **marianom said:**
> [Here]("http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html") you can find the Ubuntu Packaging Guide. Enjoy!That's almost a science in it's own right :D

---

### Post by marianom on 2007-07-09
We agree. Anyway, gabeyg can't say we didn't provide all available options!

OT: I was always curious about your country. And I plan to visit it some day. I'm sure its worth the travel to those (for me) distant lands.

---

