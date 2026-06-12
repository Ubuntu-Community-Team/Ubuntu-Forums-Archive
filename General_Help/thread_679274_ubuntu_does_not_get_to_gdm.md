---
title: "ubuntu does not get to gdm"
date: 2008-01-26
forum: General Help
---

### Post by jasonpeinko on 2008-01-26
I turn on my laptop and it boots and then instead of taking me to the login manager, i get a black screen with a flashing cursor. How do i fix this?

---

### Post by Rocket2DMn on 2008-01-26
Hit CTRL+ALT+F1 to get to a TTY, login to the terminal, then reconfigure X with
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
You will be asked a bunch of questions about your hardware, do your best to answer.

---

