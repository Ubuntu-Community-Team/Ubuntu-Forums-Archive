---
title: "Newbie x server"
date: 2006-10-29
forum: General Help
---

### Post by Lax101 on 2006-10-29
Ok im using Edgy Ifty 6.10.  What im trying to do is install the nvidia  drivers but i have no clue of how to stop x server.  Can some one tell me please.

---

### Post by ~LoKe on 2006-10-29
Open up the virtual terminal by press ctrl+alt+F1.  Log in, then type the following:
```
sudo /etc/init.d/gdm stop
```
Install the driver, then, type this:
```
sudo /etc/init.d/gdm restart
```
To get back to the GUI.

---

### Post by Lax101 on 2006-10-29
thank you that really helped me a lot i was able to install and learned a little more today.:D

---

