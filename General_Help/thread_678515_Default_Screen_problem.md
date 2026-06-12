---
title: "Default Screen problem"
date: 2008-01-25
forum: General Help
---

### Post by bayne on 2008-01-25
Recently, I was fooling around with my screens and graphics, and I changed it to an external one on accident.
I rebooted and I entered my terminal log-in, and entered, "Startx," after logging in as I normally do, but it could not find a screen. I would assume that I'm having this problem from changing the default screen.
Could anyone give me the entry to change my default screen in the terminal?

---

### Post by dcstar on 2008-01-26
> **bayne said:**
> Recently, I was fooling around with my screens and graphics, and I changed it to an external one on accident.
I rebooted and I entered my terminal log-in, and entered, "Startx," after logging in as I normally do, but it could not find a screen. I would assume that I'm having this problem from changing the default screen.
Could anyone give me the entry to change my default screen in the terminal?

```
sudo dpkg-reconfigure xserver-xorg
```
or
```
sudo nano /etc/X11/xorg.conf
```

---

