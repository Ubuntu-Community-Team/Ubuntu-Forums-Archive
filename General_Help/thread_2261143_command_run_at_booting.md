---
title: "command run at booting"
date: 2015-01-16
forum: General Help
---

### Post by mac-2check on 2015-01-16
Hello, I'm looking for a way to run a command automatically after booting. I found a few guides, but I'm not really sure how it works...

I'm setting up a laptop with xubuntu for my grandmum and I need to run the command xbacklight -set 75 at every start. 

I hope you know what I mean, thanks for help...

---

### Post by tgalati4 on 2015-01-16
Try putting it above the line "exit 0" in /etc/rc.local

Open a terminal:

```
sudo nano /etc/rc.local
```

Control-O and Control-X  to write the changes and to quit.  Then reboot and see if the backlight gets set correctly.

```
cat /etc/rc.local
```

to review the changes that you made.

---

### Post by sisco311 on 2015-01-16
The X server must run when you use xbacklight. 


If you don't need (sudo) root privileges to run the command, then add it to the startup applications (Menu -> Settings -> Session and Startup - > Application Autostart -> Add)

---

### Post by mac-2check on 2015-01-18
solved, I did in settings as sisco says. thanks ;)

---

