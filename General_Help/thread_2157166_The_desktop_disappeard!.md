---
title: "The desktop disappeard!"
date: 2013-06-24
forum: General Help
---

### Post by mbnoimi on 2013-06-24
Howdy,

I've ubuntu 12.04 after calling apt-get update;apt-get upgrade then restarted the machine I became unable to see anything except desktop wallpaper!

How can I fix this issue?

P.S. I can login throw SSH and all the installed servers work fine.

---

### Post by DeathByDenim on 2013-06-24
Does this happen before you get the normal log-in screen of after you've logged in?
You can try creating a new user account and log in using that. If that works, then there is something wonky going on with your user settings.

---

### Post by mbnoimi on 2013-06-24
> **DeathByDenim said:**
> Does this happen before you get the normal log-in screen of after you've logged in?
I set ubuntu to auti-login before this issue happen so when the machine starts up it shows me wallpaper directly.

By the way, I can call CTRL+ALT+L for locking the user.

> You can try creating a new user account and log in using that. If that works, then there is something wonky going on with your user settings.
Do I've to do that throw SSH? or there is some trick.

---

### Post by DeathByDenim on 2013-06-24
Yeah, you can create a new user through SSH. Use this command:
```
sudo useradd -U -m -G adm,dialout,cdrom,video,plugdev,lpadmin,admin,sambashare -s /bin/bash testuser
sudo passwd testuser
```
The first command creates a new user called "testuser" and the second command sets a password for that user.

Now, auto-login poses a tiny bit of a problem, but you can try press Ctrl + Alt + Shift + Delete. That's the short cut for logging out and it should get you to the login screen. That will hopefully work. If it doesn't work, I think the lock screen has a button for switching users, right?

---

### Post by mbnoimi on 2013-06-25
>  Now, auto-login poses a tiny bit of a problem, but you can try press Ctrl + Alt + Shift + Delete. That's the short cut for logging out and it should get you to the login screen. That will hopefully work. If it doesn't work, I think the lock screen has a button for switching users, right? 

I successfully create a new user and could login but all the windows appear borderless and task bar is hidden (I'm using Cinnamon)

P.S. I tried to login in Cinnamon 2d but I got same result.

---

### Post by mbnoimi on 2013-06-25
I fixed this issue by:

```
apt-get install cinnamon
```

I don't know what's going on but **** can happen

---

### Post by grahammechanical on 2013-06-25
You might have been able to solve it another way.

At that Desktop wallpaper, right click the desktop and select Change Desktop Background. That will bring you to the Appearance utility which is in System Settings. From that you can open the System Settings main page. From there open Additional Drivers and activate a video driver. You may need to experiment. That might fix this problem for the next time you boot.

Regards.

---

