---
title: "apt-get problem"
date: 2008-06-12
forum: General Help
---

### Post by hgyang on 2008-06-12
I was using gutsy n working fine but since after upgrade to hardy on the net problem exist like mic no function on SKYPE update & upgrade is denied with error : malformed line 5 in source list bluetooth no function, win XP can open -dual boot n wep password cant connected... i really need help as i am new to Ubuntu. my laptop is Dell Vostro 1400

---

### Post by cdtech on 2008-06-12
Try this on a command line:
sudo dpkg –configure -a

See if that helps....

---

### Post by drs305 on 2008-06-12
> **hgyang said:**
> malformed line 5 in source list 

If you post your sources.list we can look at it and see what the problem is:
```
cat /etc/apt/sources.list
```

---

