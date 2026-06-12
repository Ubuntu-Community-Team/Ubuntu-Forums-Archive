---
title: "Can't turn off computer through GUI"
date: 2014-02-25
forum: General Help
---

### Post by nihao123456ftw on 2014-02-25
Hello again all,

I am unable to use "Logout..." "Restart..." or "Shutdown..." options in the top right menu of the desktop interface. Clicking these options does absolutely nothing. Also, this might be related to a different problem, but i'm able to use the "Suspend" option but when turning on my computer again to go out of suspend there is no display on my monitors.

I can use the terminal to shut down ("shutdown -h now" or "poweroff" using sudo).

I think that this could be a permissions problem because I had a lot of major problems previously while trying to install proprietary graphics drivers from amd (wouldn't let me login), and in all the confusion I do remember frantically adding some +777 permissions from root to some directories related to logging in, in particular /etc/lightdm. In the end the login problem turned out that .Xauthority was owned by root so I deleted it and now it recreated itself with my user's permissions (and I can login). So now I think a similar problem is happening with this shut down problem.

(P.S another problem I have, although I don't mind it since it speeds up the login loading time, is that on the login splash screen it shows ubuntu's default  background and not the background I chose for my user account.)

---

### Post by nihao123456ftw on 2014-02-26
[SOLVED]

Ok... well just a minute ago I booted up Ubuntu and somehow "magically" my computer fixed itself. I wasn't sure if this was just a one-off or something so I rebooted 1 more time and i'm still able to shut down now :confused:. I think i remember redoing chmod 777 /etc/lightdm in my normal user account but i swear that was several logins ago... sorry that i'm not able to explain how I fixed it.

---

