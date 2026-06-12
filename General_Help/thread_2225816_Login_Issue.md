---
title: "Login Issue"
date: 2014-05-23
forum: General Help
---

### Post by satyabrata-kranti on 2014-05-23
I use **Ubuntu 14.04**. I'm not able to login to desktop after I start the system **from sleep mode**. Sometimes the **screen freezes** and whatever password I type not being shown in the password box. Even if I'm able to typed the password and try to login, it won't let me login and **comes back to the login screen again**. Finally, I'd to **manually reboot the system**.
I checked the **Xsession error logs** and got the following error which I'm not able to comprehend.
[INDENT]Script for ibus started at run_im.[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd main process ended, respawning[/INDENT]
[INDENT]init: at-spi2-registryd respawning too fast, stopped[/INDENT]
[INDENT]init: logrotate main process (18476) killed by TERM signal[/INDENT]
[INDENT]init: Disconnected from notified D-Bus bus[/INDENT]

No idea what to do. Any suggestions since it's not possible to hard reboot system every time such a thing happens.

---

### Post by s9032g@comcast.net on 2014-05-23
This sounds similar to a problem I had. After a lot of fancy advice this is the one that solved my problem:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It worked perfectly. As it works it also creates a report and gives you a numbered hyperlink to get to it if you need to see, or to pass on the detail of what happens. I found that by repairing my boot issue other problems also went away.

Good luck

---

### Post by satyabrata-kranti on 2014-05-23
thanks for your reply.

The solution that you described seems like intended for boot sector/grub repair/recovery. But mine is a login issue. It only happens when I try to log-in to desktop after starting my system from sleep mode. How this could be a boot related issue ?

---

### Post by s9032g@comcast.net on 2014-05-24
I had a login issue also. No login screen appeared.
 
I suggest that you give boot-repair-disk (create an iso) a try. I don't think you have anything to lose. The report it generates might help you find out something you need to know.

---

### Post by satyabrata-kranti on 2014-05-27
yes, I did that. It also modified my grub.cfg. But, the problem is not solved. Since it is not always happening, I don't know what to monitor and exactly when it'll show up.

---

