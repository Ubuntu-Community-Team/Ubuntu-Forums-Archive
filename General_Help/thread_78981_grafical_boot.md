---
title: "grafical boot"
date: 2005-10-19
forum: General Help
---

### Post by abiezerm on 2005-10-19
hi all

i upgrade (by apt-get upgrade from 5.4) to breezy and my boot is the same, how can i change it??

thanks

---

### Post by seldenthuis on 2005-10-19
apt-get install usplash
sudo dpkg-reconfigure usplash
sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by abiezerm on 2005-10-19
thank a lot man...

i will try later

---

### Post by abiezerm on 2005-10-19
ok works:p

---

### Post by baza41 on 2005-10-19
[QUOTE=abiezerm]ok works:p[/QUOTE]


Kool init! :p 

Baza

---

