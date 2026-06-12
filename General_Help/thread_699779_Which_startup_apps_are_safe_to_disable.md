---
title: "Which startup apps are safe to disable?"
date: 2008-02-17
forum: General Help
---

### Post by Gerontius on 2008-02-17
Hello... since i'd like to make my Ubuntu lighter (and no... i don't want to go to Fluxbox or Xfce - maybe i'd use xubuntu if i knew how to make my multimedia keys work out of the box or browse network shares directly from thunar) i'd like to know which programs can be removed from startup?

I have disabled tracker (it is a really nice program... when it works - let's hope it'll work properly in Hardy) and Evolution alarm notifier (i don't use evolution... i'm a gmail addict)

Is it safe to disable gnome power manager (i'm running a desktop computer)?

Thanks

---

### Post by 1337455 10534 on 2008-02-17
[terminal]
sudo aptitude install bum
gksudo bum

And disable what you do not use. Use common sense, you need networking, power management, and gdm etc..
Alternatively, go to System-->Preferences-->Sessions, and or System-->Administration-->Services.

---

