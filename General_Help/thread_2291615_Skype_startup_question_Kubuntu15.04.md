---
title: "Skype startup question Kubuntu15.04"
date: 2015-08-21
forum: General Help
---

### Post by rschanzenbacher on 2015-08-21
I have skype and it starts up when I log in but it opens the window so what I'm asking is can linux open skype without opening the window. (Like in windows) So only the desktop tray icon?

---

### Post by ajgreeny on 2015-08-21
In the general tab of skype's options dialogue there is a tick-box for "Start skype minimised in system tray"

That should do it! If not, I do not know of any other setting.

---

### Post by rschanzenbacher on 2015-08-21
Thx! I'm a n00b at startup applications. What if I wanted to do this with another application? Would there be a startup parameter?

---

### Post by ajgreeny on 2015-08-22
> **rschanzenbacher said:**
> Thx! I'm a n00b at startup applications. What if I wanted to do this with another application? Would there be a startup parameter?
That is totally dependent on the application, though there is a utility called alltray which you can install from normal repositories which will allow some applications to start in the system tray as an icon if started with command ```
alltray <application-command>
```Not all programs work using alltray but many do.  Just try it out to see.

---

