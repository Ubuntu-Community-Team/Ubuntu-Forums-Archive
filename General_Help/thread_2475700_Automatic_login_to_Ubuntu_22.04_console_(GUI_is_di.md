---
title: "Automatic login to Ubuntu 22.04 console (GUI is disabled)"
date: 2022-06-05
forum: General Help
---

### Post by systmworks on 2022-06-05
Hello, 
I recently installed Ubuntu 22.04 onto an spare Intel NUC I had lying around home.    Automatic login to the desktop GUI was working fine.

I have since disabled the GUI  (most of the time I wont need it, but nice to have the option to launch it) using this command:
```
sudo systemctl set-default multi-user
```

Now it asks for username and password on bootup. 
Id like to have the console automatically login and launch a single application  (so my young child can use it, without having to type a login)

Ive Googled and searched this forum, but keep finding the same posts talking about auto login to the GUI. 
I have enabled automatic login in [FONT=monospace]/etc/gdm3/custom.conf[/FONT], but I suspect this only relates to the GUI and not the console?

Any help is appreciated.

---

### Post by TheFu on 2022-06-05
Nope.

---

