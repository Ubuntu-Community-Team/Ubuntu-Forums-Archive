---
title: "LightDM ignoring configuration?"
date: 2018-02-24
forum: General Help
---

### Post by thedevilsjester on 2018-02-24
Hello,

I am trying to change the default login session and automatically log in.

After reading various online documentation, and trying half a dozen different things, I am still no closer to a solution.  Using the standard paths defined at [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM) I have tried creating a new .conf file.  In one of those directories there is already a 60-xubuntu.conf, so I add my own 60-mysession.conf (and remove the xubuntu one, to make sure its not taking priority) that is formatted in the same fashion, with the following:

```
[Seat:*]
user-session=mysession
```
Where /usr/share/xsessions/mysession.desktop is the session I am trying to default to (which works fine when I select it manually).

I deleted all of the rest of the .desktop files in the xsessions directory (to force it to default by being the only entry) and that works, though is more of a hack than a solution, but when I try and add 'autologin-user=myuser' to the configuration file (to force an auto log-in), that doesn't work either.  Its as if my configuration is being completely ignored.

My end goal is to never use the login manager/greeter.  I have one session that I always want to load, and one user that I always want to log in.  If I could bypass the whole mechanism and just go straight to the session, that would be even more ideal, but just getting LightDM to work with the configuration I am giving it should be enough.

Does anyone have any idea what might be happening?

I am using Ubuntu 17.10, installed with the Ubuntu Minimal ISO, selecting only Xubuntu Minimal Desktop.  (I did not choose to encrypt my home folder)

---

### Post by again? on 2018-02-24
I find the arch wiki to usually have the most up to date info.
 [https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin](https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin)

I tested the above method and it worked for me in Xubuntu 17.10.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] cat /etc/lightdm/lightdm.conf**
[Seat:*]
autologin-user=glen

**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] groups glen**
glen : glen adm cdrom sudo dip plugdev lpadmin sambashare autologin
```
If you're using a keyring manager you may still need to enter your password after login 
for chrome password saving.

---

### Post by ubname on 2018-02-24
IDK if it's a typo but "mysession" clearly is not equalto "mysession.desktop", also Ubuntu 17.10 have autologin option, is it not present in Xubuntu (?)

---

### Post by thedevilsjester on 2018-02-24
> **ubname said:**
> IDK if it's a typo but "mysession" clearly is not equalto "mysession.desktop"
Its not a typo, from what I can tell from both the documentation and existing files, the **.desktop** portion of the name is not used in the configuration file.  For example here is the output of the existing file **60-xubuntu.conf**
```

[Seat:*]
user-session=xubuntu
```

Where the session file is called: **xubuntu.desktop**

> **ubname said:**
> also Ubuntu 17.10 have autologin option, is it not present in Xubuntu (?)
Where would you select said option?


> **guber2 said:**
> I find the arch wiki to usually have the most up to date info.
 [https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin](https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin)

That worked for the auto login, thanks.

Oddly setting **autologin-session** to **mysession** works (it selects the correct session when logging in), but **user-session** does not work (with or without auto login)

Unfortunately when the user ends the session, they are presented with the login screen.  The goal of this is to have a single session, single user (almost like a Kiosk mode).  The user should never be presented with a login screen.  (if the session ends, the computer should just shut down).  How can I go about doing this?  I realize that this defeats the purpose of a greeter like LightDM, and if I can just bypass it entirely, that would be ideal, but not required.

---

### Post by deadflowr on 2018-02-24
> Its not a typo, from what I can tell from both the documentation and existing files, the .desktop portion of the name is not used in the configuration file. For example here is the output of the existing file 60-xubuntu.conf
```

[Seat:*]
user-session=xubuntu
```
Where the session file is called: xubuntu.desktop

You actually need the Name= name inside the .desktop file

The file might be xubuntu.desktop, but the name might be Xubuntu with a capital X.

Edit: if your mysession name is just mysession, then just ignore this.
Otherwise double check what the name is.

---

### Post by thedevilsjester on 2018-02-24
> **deadflowr said:**
> You actually need the Name= name inside the .desktop file
Looking at the existing resources xubuntu.desktop and 60-xubuntu.conf its clear that this is not the case.  Also, when I use autologin-session=, instead of user-session=, with the exact same value, it works perfectly.  This is using the **mysession** part of **mysession.desktop** not using MySession as it is defined inside of mysession.desktop.

---

### Post by again? on 2018-02-24
> **thedevilsjester said:**
> Unfortunately when the user ends the session, they are presented with the login screen.  The goal of this is to have a single session, single user (almost like a Kiosk mode).  The user should never be presented with a login screen.  (if the session ends, the computer should just shut down).  How can I go about doing this?  I realize that this defeats the purpose of a greeter like LightDM, and if I can just bypass it entirely, that would be ideal, but not required.

The solution from [HERE]("https://unix.stackexchange.com/questions/68389/need-to-auto-login-after-logout-on-ubuntu"), works for me.
It runs a script on logout which restarts lightdm thus restarting the auto-login process.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] cat /etc/lightdm/lightdm.conf**
[Seat:*]
autologin-user=glen
session-cleanup-script=/etc/lightdm/restart

**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] cat /etc/lightdm/restart**
#!/bin/bash

trap "" SIGHUP SIGINT SIGTERM
PATH=$PATH:/sbin:/usr/sbin
service lightdm restart
```

If you wan't to shutdown when the user logs out, in the "/etc/lightdm/restart" script, replace **service lightdm restart** with 
```
shutdown -P now
```

---

### Post by deadflowr on 2018-02-26
> **thedevilsjester said:**
> Looking at the existing resources xubuntu.desktop and 60-xubuntu.conf its clear that this is not the case.  Also, when I use autologin-session=, instead of user-session=, with the exact same value, it works perfectly.  This is using the **mysession** part of **mysession.desktop** not using MySession as it is defined inside of mysession.desktop.

Sorry, I'm thinking of something totally different, I just cannot remember what.
Mea culpa

---

