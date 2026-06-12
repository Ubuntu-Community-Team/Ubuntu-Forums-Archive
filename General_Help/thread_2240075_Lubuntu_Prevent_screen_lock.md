---
title: "Lubuntu: Prevent screen lock"
date: 2014-08-17
forum: General Help
---

### Post by leunam12 on 2014-08-17
hi, I have Lubuntu 14.04 on my wife's desktop. I have it set up so the screen goes blank after 30 minutes of inactivity and screen lock deactivated. It was working normal until one day it started to lock the screen on resume and I haven't been able to disable it. what can I do? I don't want the screen to lock ever for no reason.

Thanks

---

### Post by Dennis N on 2014-08-17
Are you using light-locker? You can uninstall light-locker and use xscreensaver instead. xscreensaver has the option for a 'blank screen only' after a period of time. I find it reliable. 

After installation, you need to add it to your startup applications. The command required is [FONT=Courier New]**xscreensaver -no-splash**[/FONT]

---

### Post by leunam12 on 2014-08-18
Yes, I am using light-locker. I'll try what you say, thanks

---

### Post by leunam12 on 2014-08-19
The problem has not returned, so I'm marking this thread as solved.

Thanks.

---

