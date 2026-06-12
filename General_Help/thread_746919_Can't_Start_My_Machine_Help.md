---
title: "Can't Start My Machine Help???"
date: 2008-04-06
forum: General Help
---

### Post by adn258 on 2008-04-06
As soon as I start it I get this and all I can do is login with a command prompt I get no GUI even if I use startx.  What should I do HELP?


usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu 7.10 bomb tty1


bomb login:

---

### Post by BaffledMollusc on 2008-04-06
Just to rule out the obvious first - Did you install the desktop version of Ubuntu or the server version? The server version doesn't come with a GUI by default.

Also, are you dual booting with Windows, or is Ubuntu the only operating system on your PC?

---

### Post by adn258 on 2008-04-06
> **BaffledMollusc said:**
> Just to rule out the obvious first - Did you install the desktop version of Ubuntu or the server version? The server version doesn't come with a GUI by default.

Also, are you dual booting with Windows, or is Ubuntu the only operating system on your PC?

I am using GUI ubuntu and I just recently had this problem.  Now.  The usplash thing went away and now we just get a terminal to log into.  Unfortunatly I have a lot of my programs and files on here.  What should I do?

---

### Post by ghost_ryder35 on 2008-04-06
log into the terminal (which you say you can get too) and issue this command
```

sudo dpkg-reconfigure xserver-xorg


```

---

