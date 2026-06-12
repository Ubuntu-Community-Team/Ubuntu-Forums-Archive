---
title: "problem with login"
date: 2008-05-22
forum: General Help
---

### Post by mats990 on 2008-05-22
I have changed some themes in my ubuntu 8.04 and my computer freezed after the restart, when I entered username and password nothing happened, there was only yellow background and one white rectangle. At that point username and password worked but ubuntu freezed before booting. After a few restarts i tried to fix the X server in recovery mode. since then I cannot login because it says that my username or my password is wrong. I tried to change my password in recovery mode terminal but nothing. Tried to create new admin user, also nothing... can you please help me?

ps. sry for bad english, i hope you understand my problem...

---

### Post by housam on 2008-05-22
reinstall the desktop, it mey work 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by mats990 on 2008-05-22
not working...
i got this message:
ubuntu-desktop is alredy the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

when I press fix X i get this:
xerver-xorg postinst warning: overwriting posibly-customized configuration file: backup in /ETC/X11/xorg.conf.'numbers'

---

### Post by Armagideon on 2008-05-22
Perhaps try this:

```

sudo apt-get --reinstall install ubuntu-desktop

```

---

### Post by mats990 on 2008-05-22
I reinstalled ubuntu-desktop but got the same problem.
btw, why i get the message about wrong username or password if i know they both are entered correctly?

---

### Post by mats990 on 2008-05-25
any solution?
Is it possible to reinstall ubuntu without deleting my applications?

---

