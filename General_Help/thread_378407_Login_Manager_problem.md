---
title: "Login Manager problem"
date: 2007-03-07
forum: General Help
---

### Post by zeroblitzt on 2007-03-07
Hi there.

Ever since upgrading to Edgy, my graphical boot has been messed up. The Ubuntu loading splash doesn't show up. Text is just output (not a lot of it, either). It just checks the drives, then presents the login prompt. After sitting at it for 10 seconds, GDM finally loads.

It's not vital or anything, but it is annoying.

So far the only thing I've done to try and fix it is:
```
dpkg --reconfigure usplash 
```

And the reconfiguring went fine, so I don't see why the Ubuntu splash won't load.

---

### Post by solar george on 2007-03-08
Try this,

```
sudo apt-get remove usplash-theme-ubuntu
sudo apt-get install usplash-theme-ubuntu
```

---

### Post by zeroblitzt on 2007-03-09
No luck, didn't work.

Could it have anything to do with the kernel being told to boot up in "quiet" mode? I know thats one of the things it prints out, like "splash quiet" etc.

---

