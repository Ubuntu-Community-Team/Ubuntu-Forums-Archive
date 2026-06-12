---
title: "Switching keyboard layout"
date: 2012-10-24
forum: General Help
---

### Post by komarx6 on 2012-10-24
I was searching the forums but didn't find what I was looking for.
I want to be able to switch between two different layouts in Lubuntu. I heard it is possible. But I don't even have option to add kayboard layout indicator to panel.

I read that this could help, but still I need indicator in the panel.
```
echo '@setxkbmap -option grp:alt_shift_toggle "us,sr"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart
```

What's the proper way to switch layouts in Lubuntu?

---

### Post by Rex Bouwense on 2012-10-24
See here:
[http://lxlinux.com/#17](http://lxlinux.com/#17)

---

### Post by komarx6 on 2012-10-25
It's not working. There wasn no autostart file, so I created it. It didn't work. Than I manually changed the values in /etc/default/keyboard but I don't know if it works because I don't know how to switch layouts because I don't have layout indicator.

---

