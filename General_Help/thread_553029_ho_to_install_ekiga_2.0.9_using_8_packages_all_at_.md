---
title: "ho to install ekiga 2.0.9 using 8 packages all at once?"
date: 2007-09-17
forum: General Help
---

### Post by sdowney717 on 2007-09-17
[http://ekiga.org/index.php?rub=5&path=ubuntu/feisty_x86](http://ekiga.org/index.php?rub=5&path=ubuntu/feisty_x86)

each package has various dependencies. If I try to install them individually they break or wont install.

---

### Post by YannickDefais on 2007-09-17
Hi,

The easy way:
[https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c](https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c)

Regards,
Yannick

---

### Post by FuturePilot on 2007-09-17
I think you can use Synaptic and use the Add Downloaded Packages feature. Or just download all the packages to a folder say on your desktop. Then just
```
cd Desktop/foldername/
```
and ```
sudo dpkg -i *.deb
```

---

### Post by sdowney717 on 2007-09-17
thanks

---

