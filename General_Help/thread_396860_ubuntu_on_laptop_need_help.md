---
title: "ubuntu on laptop need help"
date: 2007-03-29
forum: General Help
---

### Post by cptjaben on 2007-03-29
I just bought a new [Asus f3jp]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220141"). I'm trying to install Ubuntu on it, but when I insert a live cd it boots fine until it gets to the desktop of the live cd at which point the graphics get messed up completely. Does anyone know what one could do to possibly fix this problem, I tried 6.10 on it so far. I should hope that I won't have to switch back to windows because of this.

Thanks

---

### Post by hikaricore on 2007-03-30
You could try hitting ctrl+alt+f1

Then run through:

```
sudo dpkg-reconfigure xserver-xorg
```

Then after you finish run:

```
sudo /etc/init.d/gdm restart
```

It may not work but I've found it useful on a few systems where the video or resolution was recognized incorrectly on boot.

---

### Post by cptjaben on 2007-03-30
Thanks, i'll try that and see

---

