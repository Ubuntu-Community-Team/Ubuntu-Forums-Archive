---
title: "A way to reset ubuntu without deleting ubuntu files? Whoa! Tell me how!"
date: 2006-09-22
forum: General Help
---

### Post by UltraSonicSite on 2006-09-22
That would be great since ubuntu's login manager doesn't seem to work anymore, so is there a way to get everything to be as if it were a fresh install, but with already installed files staying there?

---

### Post by yopnono on 2006-09-23
Don't know what you have done, but... try to reconfigure/reinstall you login manager.
Reconfigure  
```
dpkg-reconfigure "+ your_login_manager"
```

Or use *--all* to reconfigure the whole lot

---

### Post by aysiu on 2006-09-23
Can you explain what you mean by "Ubuntu's login manager doesn't seem to work any more"? What exactly happens? Do you get an error? Are you able to log in at all?

---

### Post by UltraSonicSite on 2006-09-23
The GUI does not come up anymore, just a console login screen.

---

### Post by UltraSonicSite on 2006-09-23
I assume it's an easy fix? And for the command above, what IS my login manager O.O

---

### Post by aysiu on 2006-09-23
Okay, just console? Maybe this might help, then:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

P.S. If you're using Ubuntu or Xubuntu, your login manager is GDM. If you're using Kubuntu, it's KDM.

---

