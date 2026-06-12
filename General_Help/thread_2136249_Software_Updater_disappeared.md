---
title: "Software Updater disappeared"
date: 2013-04-17
forum: General Help
---

### Post by johncroc on 2013-04-17
Hello all,

I built a new machine this afternoon, installed Ubuntu on it, noticed there were a number of updates to be installed.  opted to first install the proprietary drivers for my Nvidia video card, rebooted, and now the Ubuntu software updater is gone from the dock and even if I try the dash, I can't find it.

How can I get it back?

---

### Post by dino99 on 2013-04-17
open a terminal, and run : 
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by johncroc on 2013-04-17
> **dino99 said:**
> open a terminal, and run : 
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

It looks to me as if those commands (handy to know, by the way!) did what the Software Updater would have done (Is that correct?), but how do I get the icon back?  Where did it go?  What might have caused it to disappear in the first place?  Is there something I can do/avoid that will prevent it disappearing in the future (assuming I can get it back)?

---

### Post by ibjsb4 on 2013-04-17
Heres a few places to go.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

[http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html](http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html)

Also in terminal:

```
man apt-get
```

and

```
man dpkg
```

---

### Post by dino99 on 2013-04-17
into a terminal:

compiz --replace -a &
setsid unity

---

