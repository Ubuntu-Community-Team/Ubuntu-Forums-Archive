---
title: "startup"
date: 2007-01-08
forum: General Help
---

### Post by n8ek on 2007-01-08
When i startup kubuntu i get a black screen and can only get Kubuntu up and running by typing startx is there a way of getting it to startup normally? i have the latest nvidia driver installed and beryl installed aswell (the problem started before the nvidia&beryl install/update

Thanks in advance

---

### Post by taurus on 2007-01-08
Try to reinstall kdm again to see if that helps.

```
sudo aptitude remove kdm
sudo aptitude update
sudo aptitude install kdm
sudo /etc/init.d/kdm start
```

---

### Post by n8ek on 2007-01-08
thanks for that but it has made the problem worse i have now lost my Kmenue and it looks more like Mandriva than Kubuntu, whats gone wrong

thanks

---

### Post by taurus on 2007-01-08
Did you install Kubuntu from a CD (Dapper or Edgy)?

---

### Post by n8ek on 2007-01-08
from a cd dapper version

---

### Post by n8ek on 2007-01-08
as i type this the laptop where kubuntu is installed has rebooted (i did that ) and stalled at a black screen with a white blinker totally unresponsive

---

### Post by taurus on 2007-01-08
Boot into recovery mode from the GRUB menu and at the prompt, reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
/etc/init.d/kdm start
```

---

### Post by n8ek on 2007-01-08
when i type this (/etc/init.d/kdm start) it tels me there is no sutch file

thanks

---

### Post by taurus on 2007-01-08
Did you reinstall kdm again after you removed it?

```
sudo aptitude update
sudo aptitude install kdm
sudo /etc/init.d/kdm start
```

---

### Post by n8ek on 2007-01-08
yeah did that but i still have no kmenue (/etc/init.d/kdm start) and it tells me that does not exist

---

### Post by taurus on 2007-01-08
```
sudo aptitude install kubuntu-desktop
```

---

### Post by n8ek on 2007-01-08
that worked it no longer looks like mandriva still got no kmenue new install i think?

---

