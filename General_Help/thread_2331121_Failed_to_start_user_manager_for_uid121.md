---
title: "Failed to start user manager for uid121"
date: 2016-07-18
forum: General Help
---

### Post by Malecord on 2016-07-18
Hello,

I had this error coming out of nothing during startup 2 days ago. The startup loops on trying to start the user manager for uid121 again and again.

```
Failed to start user manager for uid121
```

I was previously running the 15.04 with propietary nvidia drivers and I never had a problem. When this thing appeared since I wanted to upgrade I took the chance to wipe the disk and install a fresh 16.04. Unfortunately this error appears again when I enable the proprietary drivers (any version) apparently.

Is this a problem of user permissions or something? Any idea of what's going wrong there? In my old install this appeared out of nothing, I had not touched the drivers since a year or something.

Thanks,

Mal

---

### Post by deadflowr on 2016-07-19
You figure out more by looking at the actual 121 user.
```
getent passwd
```
will show you all users, and
```
getent passwd  | grep 121
```
should show just that user, for simplicity.

---

### Post by Malecord on 2016-07-20
Hei deadflowr,

thank for the suggestion. The problem was that I had no way to exit the loop (manager started, manager fail to start, start, fail, start, fail... ) and the system was not yet initialized so no way to access a terminal.

So what I did was to re-install a fresh 16.04 and this time I installed Nvidia drivers from command line. There were some errors left so I had to run a dpkg reconfigure. But now it runs and apparently it's stable.

Maybe when I installed the drivers with the Ubuntu GUI utility I missed some errors and left the system inconsistent? Or maybe the fact that the securboot was somehow set to Windows was causing the problem (but only with nvidia drivers). Either one of the two or both. Actually I can make a try and switch back securboot to windows just to check, I'll doit tonight.

Thanks anyway.

Mal

---

