---
title: "Weird nvidia brightness issue."
date: 2013-05-03
forum: General Help
---

### Post by zero2xiii on 2013-05-03
Hay all,

When I switch to any TTY terminal (ctrl + alt + F1-6) and back to unity (F7) my nvidia-settings's brightness is reset to zero. I always take it down to about -0.30.

How can I find what is causing this? It is really eritating as I love to script in a TTY using nano and not get distracted by all the other things on my computer.

relevant info:
uname -a:
```
3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
lsmod | grep nvidia:
```
nvidia              11308613  40
```
lspci | grep NVIDIA
```
VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS] (rev a1)
```

No output generated in dmesg that I notice.

If you need more info please ask. 

Cheers

---

### Post by pqwoerituytrueiwoq on 2013-05-03
i haver had this issue on my old laptop, although i did this, so that may be why
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
that guide is old but i have been using it since 10.04 and am now using 13.04, it sill works
looks like there is a script here that makes it faster to get it done
[http://askubuntu.com/questions/60192/after-fixing-boot-resolution-due-to-nvidia-driver-install-login-resolution-is](http://askubuntu.com/questions/60192/after-fixing-boot-resolution-due-to-nvidia-driver-install-login-resolution-is)

---

### Post by zero2xiii on 2013-05-04
Hay,

Thanks for the links, but I have non of those issues mentioned in the links. I have tried following them in anyway, but the issue still persist. Switching to a TTY, loging in and switching back to the GUI my brightness is reset to 0.00. It really is strange. As the "re load" of the GUI seems to trigger this, I assume it has to be in some lower "default" settings. For more information. Logging out and back in (in the GUI) without adjusting the brightness it automatically goes back to the "correct" value, -0.30.

Weird.

---

### Post by pqwoerituytrueiwoq on 2013-05-04
maybe you can use the lightdm display-setup-script to run xbacklight and cat a log with the brightness in it
```
~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
greeter-setup-script = /usr/local/bin/greeter-setup-script
session-cleanup-script = /usr/local/bin/session-cleanup-script
session-setup-script = sh -c '/usr/local/bin/session-setup-script &'
#display-setup-script =
```
This is what i use to rest the brightness when i boot up
```

~$ cat /usr/local/bin/greeter-setup-script 
#/bin/sh
numlockx on
if [ -f /var/log/backlightx ];then 
    xbacklight -set $(($(cat /var/log/backlightx)*10))
fi

```
```

~$ cat /usr/local/bin/session-cleanup-script 
#!/bin/bash
backlightx --get current > /var/log/backlightx

```
here is the backlightx script
[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g)

---

### Post by zero2xiii on 2013-05-04
Hay,

Thanks for the feedback but that script does not work on my system. Non of those directories or files really exist on my system. :(

Also, it is INSIDE the nvidia-settings tool the brightness is set, and is it screen brightness not the back light. (as in a laptop). If that would make a difference to the above post.

This really is boggeling my mind. I guess I can turn down the screen brightness on the screen itself and leave the system on all zero.

Do anyone know how to get nvidia logs? Or view the output of verbose or debug detail on the drivers?

Thanks so far.

---

### Post by pqwoerituytrueiwoq on 2013-05-05
the nvidia-smi commant may have something useful

---

