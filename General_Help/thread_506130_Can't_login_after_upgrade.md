---
title: "Can't login after upgrade"
date: 2007-07-21
forum: General Help
---

### Post by LouisvilleLIP on 2007-07-21
When logging in, my laptop used to blink a couple times, then send me back to the login screen.  After 5 or 6 attempts, it would let me in with the proper resolution.  Compiz worked.

I upgraded compiz recently, and now can't login.  I'm not real sure where to look for the problem.  Please help...

---

### Post by dougfractal on 2007-07-21
restore your xorg.conf from rescue or teminial and start again. If you are using svn compiz wait a day for fix or  use ubuntu's.

---

### Post by LouisvilleLIP on 2007-07-21
It looks like my situation is the same as before the upgrade.  I have since been able to login to Ubuntu even though I didn't make any changes to xorg.conf.  

I suppose my real problem is that I cannot login to Ubuntu intermittently.  5 out of 6 times, it blinks a couple times and then sends me back to the login screen.  How do resolve this?

---

### Post by dougfractal on 2007-07-21
press [ctl]+[alt]+[f1] to goto treminal
login
type

ls /etc/X11/xorg.conf*

if there's a backup  or datestamp xorg.conf file


then ```
sudo cp  /etc/X11/xorg.conf.[backup] /etc/X11/xorg.conf
```

else ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
NOTE: to remember the command "less /etc/X11/xorg.conf" its in the file.

press [ctl]+[alt]+[f7] to goto graphical

---

### Post by dougfractal on 2007-07-21
More info: card + moniter

cat /etc/X11/xorg.conf

---

