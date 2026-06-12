---
title: "Application install fails no error message"
date: 2017-06-12
forum: General Help
---

### Post by 7dEfOk4AgU on 2017-06-12
I have an odd situation, I attempt to install an application from the Ubuntu Software Centre I click on the Install button and nothing happens no error message nothing the screen almost looks unresponsive. This is on Ubuntu 17.04 on a 2016 Inspiron i7 Laptop. This has been various applications tried from the store.

---

### Post by wildmanne39 on 2017-06-13
It is a bug that has been fixed, you may have to turn on the proposed repository then do:
```
sudo apt update
sudo apt dist-upgrade
```
Reboot and you should be able to install .debs from any source, I use gdebi but that is my preference.

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1672424](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1672424)

---

### Post by 7dEfOk4AgU on 2017-06-13
You are absolutely right I forgot that. Doh!!!! Thanks heaps for the gentle reminder.

---

### Post by wildmanne39 on 2017-06-13
Your welcome, Enjoy!:)

---

