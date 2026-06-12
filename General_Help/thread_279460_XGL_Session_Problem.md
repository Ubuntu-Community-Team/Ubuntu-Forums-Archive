---
title: "XGL Session Problem"
date: 2006-10-18
forum: General Help
---

### Post by iseebluuue on 2006-10-18
alrighty, so i followed the steps outlined here 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

to install xgl and beryl on my laptop. i followed the first option for enabling xgl and beryl on login and xgl is now my default. the problem is when i click the log off button my only options are: log out, lock screen, switch user, hibernate. there is no option to shut down, restart, or suspend. so i have to log out and then shutdown from the login screen which is pretty annoying.

any ideas how to fix this? thanks

---

### Post by Cable on 2006-10-18
It's a known bug, and I'm not aware of any fixes for it.  I had this problem back when I used XGL/Compiz and never solved it.  For the time being you'll probably have to just deal with it unfortunately.

---

### Post by nikhilk on 2006-10-18
The terminal can help in this case.
You should be able to directly shutdown your machine using
```
sudo poweroff
```
and directly reboot using
```
sudo shutdown -r now
```

---

### Post by iseebluuue on 2006-10-18
thanks. i guess that'll have to do until this gets fixed

---

### Post by Jolly Roger on 2006-10-18
Check out this thread on the Beryl forums for how to make a script that will use a GUI for shutting down and rebooting. It's a hack-ish way of fixing the problem but it works until an official fix comes along.

[http://forum.beryl-project.org/post-39922](http://forum.beryl-project.org/post-39922)

---

