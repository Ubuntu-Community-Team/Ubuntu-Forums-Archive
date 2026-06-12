---
title: "DVDs played before, not now!"
date: 2006-11-21
forum: General Help
---

### Post by Chrono86 on 2006-11-21
Hey guys~
I'm on Ubuntu 6.10. I used Automatix2 to install the dvd codecs a while back and after that Totem movie player played dvds just fine. But it seems that ever since I installed the KDE desktop yesterday (but I'm still using GNOME) that Totem reports I don't have the libdvdcss codecs installed. Other players play the dvd no problem but Totem is the only player that seems (or, seemed anyways) to go to the dvd menu first, all the other players jump right to the movie itself...I'd rather use Totem if I can.

I tried unintalling and resintalling the codecs through Automatix2 but nothing has helped...any idea as to what happened?

Thanks
Adam

---

### Post by cantormath on 2006-11-21
> **Chrono86 said:**
> Hey guys~
I'm on Ubuntu 6.10. I used Automatix2 to install the dvd codecs a while back and after that Totem movie player played dvds just fine. But it seems that ever since I installed the KDE desktop yesterday (but I'm still using GNOME) that Totem reports I don't have the libdvdcss codecs installed. Other players play the dvd no problem but Totem is the only player that seems (or, seemed anyways) to go to the dvd menu first, all the other players jump right to the movie itself...I'd rather use Totem if I can.

I tried unintalling and resintalling the codecs through Automatix2 but nothing has helped...any idea as to what happened?

Thanks
Adam

You might what to check with arnieboy on this, but I believe there is a separate automatix for Kubuntu or KDE.

---

### Post by Chrono86 on 2006-11-21
I'm actually not using KDE at all, I had it installed just to have it on my system haha.

But why would installing KDE effect the libdvdcss codecs in GNOME?

---

### Post by arnieboy on 2006-11-21
> **Chrono86 said:**
> I'm actually not using KDE at all, I had it installed just to have it on my system haha.

But why would installing KDE effect the libdvdcss codecs in GNOME?

this is interesting.. 
what does:
```
sudo apt-get install totem-xine 
```
give?

---

### Post by arnieboy on 2006-11-21
> **cantormath said:**
> You might what to check with arnieboy on this, but I believe there is a separate automatix for Kubuntu or KDE.

AX2 is universal (works on Gnome/KDE/XFCE) with DE specific options.

---

