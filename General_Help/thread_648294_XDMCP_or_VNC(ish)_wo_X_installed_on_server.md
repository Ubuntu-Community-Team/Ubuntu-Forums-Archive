---
title: "XDMCP or VNC(ish) w/o X installed on server"
date: 2007-12-23
forum: General Help
---

### Post by survient on 2007-12-23
I have a server I'm trying to setup, but I don't want to put X on it if I can help it. What I'd like to do is use another desktop to access the computer in a GUI interface, using the desktop's  X server to run the GUI processes, but still "login" to the server. Basically manipulate the server remotely using a gui interface, without having X installed on it. I am aware of webmin, however I'd prefer something like a windows manager or a desktop. Is there any way to pull this off?

---

### Post by dkirk on 2007-12-23
You could ssh on to the server and then run the GUI application over the ssh session.  The application should display on the X Server running on your desktop.

```
ssh -X server
```

The only problem is that most servers that don't install an X server also don't install any GUI applications.  Hopefully the GUI applications you want to install don't have X as a dependency.

---

