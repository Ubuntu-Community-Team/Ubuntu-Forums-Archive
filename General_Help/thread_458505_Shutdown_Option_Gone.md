---
title: "Shutdown Option Gone??"
date: 2007-05-29
forum: General Help
---

### Post by blade22 on 2007-05-29
Hi, I've had this problem for the past few days. Basically when I try to shut down the computer (Ubuntu feisty fawn) the "turn off" computer option is missing?? I have options such as hibernate and suspend and log out. I just don't have the shut down option. This is particularly annoying because I don't like turning the computer off manually from the switch. Is it a configuration gone wrong??

ANY HELP IS APPRECIATED THANK YOU!

---

### Post by icarius on 2007-05-29
One option is to shutdown via terminal using *sudo shutdown -h now*. I had the same problem a while ago and it ended up being an issue with user rights with shutdown in the taskbar, which you might want to check.

---

### Post by blade22 on 2007-05-29
Thanks for the response. I'll try your method. But just out of curiosity, what kind of rights are you talking about. I've edited the user and groups so that I am part of the root group and my privileges include everything now. Unfortunately this hasn't helped me. Was this what you had in mind??

---

### Post by blade22 on 2007-05-29
Okay, I tried to shutdown via the terminal method and it gives me this message "shutdown: time expected" then asks me to try the help options. Is this normal???

---

### Post by dbott67 on 2007-05-29
The shutdown command requires a 'time' element (such as [COLOR=Blue]*now*[/COLOR], [COLOR=Blue]*+m*[/COLOR] for m # of minutes or [COLOR=Blue]*hh:mm*[/COLOR] for a specified time such as [COLOR=Blue]*23:00*[/COLOR] for an 11:00pm shutdown).

The command below will force the computer to shutdown and reboot (-r) in 5 minutes:
```
dbott@feisty:~$ [COLOR=Red]**sudo shutdown -r +5**[/COLOR]
Password:

Broadcast message from dbott@feisty
        (/dev/pts/0) at 20:32 ...

The system is going down for reboot in 5 minutes!
```If you use -h instead of -r, the system will halt (rather than re-boot).  So, as icarius notes above, to force an immediate shutdown use:
```
sudo shutdown -h now
```As for why the commands disappeared, did you recently install Beryl?  If so, try these links:

[http://ubuntuforums.org/showthread.php?p=2513503](http://ubuntuforums.org/showthread.php?p=2513503)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/93551](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/93551)

-Dave

---

### Post by blade22 on 2007-05-30
Thank you so much! I followed the second of the two links you provided and it worked!! I can finally shutdown my computer normally!! Cheers! :p

---

### Post by dbott67 on 2007-05-30
Glad it worked. Was it the **XGL hack**:
> 
Assuming you are using XGL, this is a known error. However, there is a workaround.
Your startxgl.sh file should be as follows:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```or the **Login Window** setting:

> This bug has been fixed by using the following process:

1. **System -> Administration -> Login Window**
2. On the **Local** tab under "Menu Bar" the option "Show Actions menu" has to be enabled.

This resolves the issue on both the shutdown button screen and on the login/gdm screen.  However this is a fix of the symptoms, the problem appears to be either a theme or gdm theme has the ability to change this setting.-Dave

---

### Post by Alien.col on 2008-03-04
For me it was the login window show actions checkbox.

---

### Post by Dewni on 2008-05-29
The login window show actions checkbox worked for me. I lost shutdown and reboot buttons after installing a gdm theme. So it seems to be some setting that a theme can change when installing.

---

