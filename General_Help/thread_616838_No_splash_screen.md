---
title: "No splash screen"
date: 2007-11-18
forum: General Help
---

### Post by BlueStreak69 on 2007-11-18
For some reason when I start my computer, I see grub loading but then while Ubuntu loads it is blank until it reaches the login screen. How do I make it so it shows the splash screen? Please try to explain in full detail if possible. Thanks.

---

### Post by Beaucephus on 2007-11-18
make sure usplash is installed.  It was not for me when installing gutsy
```
sudo apt-get install usplash
```

---

### Post by markusf21 on 2007-11-18
Try this:```
gksu gedit /etc/usplash.conf
```
and make sure it's not trying to use a resolution you monitor can't handle

---

### Post by erfahren on 2007-11-18
this thread may help
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

