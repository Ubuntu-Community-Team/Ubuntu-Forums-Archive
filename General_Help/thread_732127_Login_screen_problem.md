---
title: "Login screen problem"
date: 2008-03-22
forum: General Help
---

### Post by Dakillakan on 2008-03-22
Ok, I have been running Ubuntu FF for a while know with only a few problems that I have had to deal with.  But now all of a suddent I booted up my computer and it makes it to the login screen, but then the login screen seems to constantly refresh without enought time for me to imput anything.  Any help would be awesome.

---

### Post by jken146 on 2008-03-23
Could be a graphics mis-configuration.  Ctrl+Alt+F1 will bring you to a console.  Log in and do ```
sudo /etc/init.d/gdm stop
``` then ```
sudo dpkg-reconfigure xserver-xorg
``` then ```
sudo /etc/init.d/gdm start
```

---

### Post by Dakillakan on 2008-03-25
Thanks for the help, but it still did not work.

---

