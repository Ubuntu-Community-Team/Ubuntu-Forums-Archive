---
title: "Problem in installing a new OS on virtualbox"
date: 2013-03-08
forum: General Help
---

### Post by Dr.Fayed on 2013-03-08
That is what happens ..

[ATTACH=CONFIG]239927[/ATTACH]


And this is the log file ..

[ATTACH=CONFIG]239928[/ATTACH]

---

### Post by Cheesemill on 2013-03-08
The command needs to be run with root permissions...
```
sudo /etc/init.d/vboxdrv setup
```

If it still doesn't work then make sure that you have the correct kernel headers installed...
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Dr.Fayed on 2013-03-08
Still the same error message ..
After trying the second code ..

---

### Post by Cheesemill on 2013-03-08
Can you copy and paste here exactly what commands you are trying and the exact output please.

---

### Post by SVEN1 on 2013-03-09
What happens to me, when there is a kernel update. The OS will not load and then get a kernel error.It's an easy fix. Just reinstall vbox, everything will be like it was. So you might want to try reinstalling VB.

---

