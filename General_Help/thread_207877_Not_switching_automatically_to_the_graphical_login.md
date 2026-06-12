---
title: "Not switching automatically to the graphical login interface"
date: 2006-07-02
forum: General Help
---

### Post by Kikoolol on 2006-07-02
Hello everybody,

After upgrading to dapper, I got this little issue : when my kubuntu has finished loading, it shows me a console login (tty1) instead of the usual graphical login. I have to press ctrl+alt+F7, and the graphical login interface appears, so I can login in graphical mode.

Any idea to solve this very little (but boring) issue ? I've tried the usual "dpkg-reconfigure xserver-xorg" or "dpkg-reconfigure kdm" with no success. I use the nvidia proprio drivers with a 2.6.17.3 kernel.

Thks in advance,

KKl

---

### Post by zxee on 2006-07-02
What is the default runlevel listed in /etc/inittab? It should be set to 4.
Hope that helps.

---

### Post by Kikoolol on 2006-07-02
It was set to 2, but setting it to 4 didn't fix it. Thank anyway zxee ;) 

This issue is very weird because the x server and kdm are launched properly ! I don't know how kubuntu switch on the graphical login screen, maybe I have deleted a script who was doing this in the init.d directory ?

KKl

---

### Post by Kikoolol on 2006-07-04
Hum, nobody has encoutered the same issue ?

After some investigations, I would say that it's usplash-related, because when usplash is deactivated, it works fine. I tried a "dpkg-reconfigure usplash", without any success ...

KKl

---

### Post by lepre on 2006-07-05
i have a similar issue but on shutdown/reboot.
when i do it switch automatically to tty1 and after some seconds (10) it shows usplash, but it worked some time ago..

---

### Post by Ramses de Norre on 2006-07-05
[QUOTE=zxee]What is the default runlevel listed in /etc/inittab? It should be set to 4.[/QUOTE]
The default runlevel in ubuntu is 2, so I'd change it back to that.

What's the output of ```
ls -l /etc/rc2.d/|grep -i gdm
``` (or kdm if you use kde) ?

---

### Post by Kikoolol on 2006-07-05
The issue is solved ! I've made some cleaning with deborphan, there were some old breezy libs who where still in the place, then when I rebooted, everything worked fine ! That was a pretty nice collateral effect 8-) 

Nevertheless, thks for your support :D 

KKl

---

