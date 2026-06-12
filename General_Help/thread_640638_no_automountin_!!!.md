---
title: "no automountin !!!"
date: 2007-12-14
forum: General Help
---

### Post by rathin on 2007-12-14
i have got a problem that in my gutsy the automounti of other drives have just stopped..Durin bootup it just stands still wen checkin on the other drives available..so i just kill the process and then it continues with the other startup requirements..

---

### Post by taurus on 2007-12-14
What driver does it have problems with?  Open a terminal and post the outputs of these two commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

---

