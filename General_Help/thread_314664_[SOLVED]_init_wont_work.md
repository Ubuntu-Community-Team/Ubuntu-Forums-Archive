---
title: "[SOLVED] init wont work"
date: 2006-12-07
forum: General Help
---

### Post by nga911 on 2006-12-07
hi, am trying to install the nvida driver but **init** wont work :( , is there any thing am suppose to install first to make it work :confused: :confused: 
i need a fast way ... am new to ubuntu all my past distros were able to do **init** ](*,) ](*,)

---

### Post by po0f on 2006-12-07
nga911,

If you need to just stop X while installing the NVIDIA drivers, log in on a virtual console (Ctrl + F1-6) and type the following:
```
[FONT="Courier New"]$ sudo /etc/init.d/gdm stop[/FONT]
```
After you have installed the driver and have configured /etc/X11/xorg.conf, you can restart X with:
```
[FONT="Courier New"]$ sudo /etc/init.d/gdm start[/FONT]
```

---

### Post by nga911 on 2006-12-08
](*,) ](*,) i tryed what you sayed and evry thing became black :confused: it dosent acsept any command :evil: had to restart and boot to windows :( ....i think it died 	:-({|=

---

