---
title: "uswsusp as default in Unity"
date: 2015-11-25
forum: General Help
---

### Post by metinkale38 on 2015-11-25
Hey, 

i am using Ubuntu 15.10 with Unity. 

My Hibernation does only work with uswsusp, so i have to set the default Unity Hiberbate/Suspend Functions to uswsusp, how i do that? 

Google only gives me solutions for older Ubuntu versions, which do not work on mine...

---

### Post by Matej_Kov on 2016-02-29
Finally after two days of trying to get it work I found it 

[https://wiki.archlinux.org/index.php/Uswsusp#With_systemd](https://wiki.archlinux.org/index.php/Uswsusp#With_systemd)

just find out if path is /usr/lib/systemd/systemd-sleep or just /lib/systemd/systemd-sleep or other, I am using debian jessie, not ubuntu [second one for debian]

ps you dont need to copy files, just comment out or delete the replaced line

---

