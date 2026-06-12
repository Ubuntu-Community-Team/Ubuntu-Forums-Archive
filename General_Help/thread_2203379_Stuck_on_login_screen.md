---
title: "Stuck on login screen"
date: 2014-02-03
forum: General Help
---

### Post by Mirk0 on 2014-02-03
I have only one user account on Lubuntu 13.10 and the automatic access was enabled. I decided to change this option, I wanted to see the login screen on startup where I can choose the user and run the session only typing my password. I went to *Menu > Preferences > Default applications for LXSession > Settings* and ticked the *Upstart Session* option. After reboot I can see the login screen, I can choose between my account and the guest one, I select my account, I type the password, it takes it, it seems for one second to load the session, the panel... but it takes me immediately back to the login screen! I can't get in my account anymore! I guess I have to modify (with a live session) some files in */usr/share/upstart/session* folder, but I don't know how. Or maybe I can login my account in another way, then change the *Upstart Session* option!
I wish someone could help, thanks in advance.

---

### Post by PotatoHead007 on 2014-02-03
Hi Mirk0!
I have almost no experience with Lubuntu, but it should be quite easy once you know what to do. When you go into login, do Ctrl+Alt+F1. Login, then run:
```
sudo service lightdm start
```
This may do something, may not. 
If it does not:
login like i said above.
Do the following:
```

cd /usr/share/upstart/session
ls

```
Then post output here. What this does is show what files there are in /usr/share/upstart/session. As i said, i am not experienced with this, so i have to see what is there in order to understand.

---

### Post by Mirk0 on 2014-02-03
Hi, thank you for your answer!

I did what yuo asked.

```
mirko@lubuntu~$ sudo service lightdm start
start: Job is already running: lightdm
```

Here there is the content of */usr/share/upstart/session* folder.

```

at-spi2-registryd.conf
dbus.conf
im-config.conf
logrotate.conf
lxsession.conf
re-exec.xonf
ssh-agent.conf
unicast-local-avahi.conf
update-notifier-cds.conf
update-notifier-crash.conf
update-notifier-hp-firmware.conf
update-notifier-release.conf
upstart-dbus-session-bridge.conf
upstart-dbus-system-bridge.conf
upstart-event-bridge.conf
upstart-file-bridge.conf
xsession-init.conf

```

Tonight (I live in Europe) I will restore my OS with a fresh install, I needed to do this before this problem appeared, but if we want we can find anyway a solution to the problem, this solution could be useful to someone.

---

### Post by PotatoHead007 on 2014-02-03
Ok thanks, before you restore, could you please do:
```

cd /usr/share/upstart/session
cat upstart*
```
That would be very helpful, and i don't know whats in them :P

---

### Post by Mirk0 on 2014-02-03
Hey, I fixed it!

I didn't try your code, sorry but I think it is unhelpful, I modified the *desktop.conf* file for my account, it is located here:
```
/home/<username>/.config/lxsession/Lubuntu/desktop.conf
```

I disabled the *Upstart Session* only by modifying this line (obviously from true to false)!
```
upstart_user_session=true
**upstart_user_session=false**
```

Thank you very much for your help, solved!

---

### Post by PotatoHead007 on 2014-02-04
Well done on that :D

---

