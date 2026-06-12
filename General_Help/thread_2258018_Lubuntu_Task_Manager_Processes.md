---
title: "Lubuntu Task Manager Processes?"
date: 2014-12-24
forum: General Help
---

### Post by fall2 on 2014-12-24
I'm new to Ubuntu baised OS, I want to kill processes I do not use. In the task manager there are 35 processes but there are no descriptions of what they are. I basically need a list of Lubuntu Processes, descriptions of them and any dependencys. Then I'll know if I its safe to Kill them.

Oh I forgot, I'm running 14.04 version 32 bit.

---

### Post by ajgreeny on 2014-12-24
You can do part of this more easily by installing bum (**B**oot-**U**p-**M**anager) and running that will give you more info on services and processes running by default.

Killing them after bootup is not the best way to proceed; better to stop them running in the first place.

---

### Post by fall2 on 2014-12-24
I just got Boot Up Manager but hardly any of the running services in Task Manager are in there, as in there was only 1 that I could turn off. Anyway I found out I have a little problem with task manager, it does not terminate, kill or set priority to my processes. I try but nothing happens.

---

### Post by vasa1 on 2014-12-24
> **ajgreeny said:**
> ...
Killing them after bootup is not the best way to proceed; better to stop them running in the first place.
While that maybe true, won't that be system-wide and possibly be reversed when the software for responsible for the process is updated?

I kill a few processes which I don't need by placing pkill commands at the end of my ~/.config/openbox/autostart:```
(sleep 10s && pkill blueman-applet) &
(sleep 30s && pkill applet.py) &
(sleep 30s && pkill update-notifier) &
(sleep 30s && pkill light-locker) &

```

---

### Post by fall2 on 2014-12-24
> **vasa1 said:**
> 
I kill a few processes which I don't need by placing pkill commands at the end of my ~/.config/openbox/autostart:```
(sleep 10s && pkill blueman-applet) &
(sleep 30s && pkill applet.py) &
(sleep 30s && pkill update-notifier) &
(sleep 30s && pkill light-locker) &

```

Light locker is just a screen saver. I would like to disable that but I am new to placing commands I don't know were to start. Open a terminal?

---

### Post by fall2 on 2014-12-24
My task manager works again, I had to delete and download, simple. I killed Light Locker from Task Manager but I would still like to know how to kill with a command and if anyone knows were I could find a answer for my original question that would be the best.

The priority feature does not work in Task Manager but everything else does.

---

### Post by ajgreeny on 2014-12-24
You can stop light-locker from even starting by removing the file called Screenlocker from ~/.config/autostart or simply by using the menu item for **"Default applications for Lubuntu session**" or some similar title (I can't remember exactly how it's named and I'm on Xubuntu now).

It is also worth looking to see what else is in that folder and then seeing if you want any of those stopped before they start, some of which may also be in that .config/autostart folder.

---

### Post by fall2 on 2014-12-25
> **ajgreeny said:**
> You can stop light-locker from even starting by removing the file called Screenlocker from ~/.config/autostart or simply by using the menu item for **"Default applications for Lubuntu session**" or some similar title (I can't remember exactly how it's named and I'm on Xubuntu now).

It is also worth looking to see what else is in that folder and then seeing if you want any of those stopped before they start, some of which may also be in that .config/autostart folder.

Thanks I deleted that file but for some reason light locker still shows up in task manager.

---

### Post by oldos2er on 2014-12-25
> **fall2 said:**
> Thanks I deleted that file but for some reason light locker still shows up in task manager.

You probably need to logout and login again, or reboot to start a new session.

---

### Post by fall2 on 2014-12-25
> **oldos2er said:**
> You probably need to logout and login again, or reboot to start a new session.

no I tryed, lightlocker is immortal.

---

### Post by oldos2er on 2014-12-25
You can always uninstall it if you really don't want it. ```
sudo apt-get remove light-locker
```

---

### Post by fall2 on 2014-12-25
> **oldos2er said:**
> You can always uninstall it if you really don't want it. ```
sudo apt-get remove light-locker
```
Thanks, it worked. I'm so new to ubuntu systems it took me a while before I knew I had to open a Term and just copy it into their.

---

### Post by oldos2er on 2014-12-26
Ah, sorry about that, I should've been more specific about running a terminal command.

Could you please mark the thread as 'Solved' under Thread Tools at the top of this page? Thanks.

---

