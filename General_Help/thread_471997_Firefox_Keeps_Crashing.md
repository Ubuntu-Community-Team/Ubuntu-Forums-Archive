---
title: "Firefox Keeps Crashing"
date: 2007-06-12
forum: General Help
---

### Post by runoverbobby on 2007-06-12
I'm using Kubuntu Feisty with KDE, and firefox tends to freeze very often. I'm usually forced to kill the process on KSysGuard. The only firefox add-on i'm using is the human theme provided by ubuntu. Also, I'm using the Beryl window manager, but firefox was already crashing before I installed Beryl. Any suggestions?

Unrelated question: my GRUB menu at startup now has 2 different options for Linux. One of them is Ubuntu ___.15, and the other is __.16. (don't quote me on that, but I do know that the numbers are definitely different). Is this a result of normal upgrades?

---

### Post by CautionaryX on 2007-06-12
I can't fix your firefox issue, but I can tell you that having the two startup options for linux is perfectly safe. Ubuntu by default keeps a backup of (up to 4?) previous Linux kernels in case something breaks. 

In fact, did firefox have issues crashing on the previous kernel (the newest kernel is located at the top of the boot menu)? Maybe the kernel update is making it crash. (I really have no idea though.)

---

### Post by runoverbobby on 2007-06-12
> **CautionaryX said:**
> In fact, did firefox have issues crashing on the previous kernel (the newest kernel is located at the top of the boot menu)? Maybe the kernel update is making it crash. (I really have no idea though.)

Thanks for the info on the kernels ;). That makes sense.

Firefox did have issues on the previous kernel, but it didn't seem to happen as frequently. I'm using the newest one right now, and it crashed 3 times in less than 10 minutes. I like Firefox better than Konqueror, so I'd like to try to fix it somehow. Installing it again didn't fix it.

---

### Post by runoverbobby on 2007-06-12
edit: now i'm having the same problem with Konqueror. It seems to be a general problem with my browsers

---

### Post by unibok on 2007-06-19
I am also running Feisty with KDE and have the same problem. It seems to me that it has something to do with Flash and not Firefox itself. Every time there is a flash content displayed or loading there is a chance that Firefox crashes as soon as I try to leave the page - it must be a bug in some kind of a flash.unload or similar function.

I did install flash plugin via Automatix. Maybe that was mistake. Will uninstall and try another way and will let you know.

---

### Post by Crafty Kisses on 2007-06-19
> **runoverbobby said:**
> I'm using Kubuntu Feisty with KDE, and firefox tends to freeze very often. I'm usually forced to kill the process on KSysGuard. The only firefox add-on i'm using is the human theme provided by ubuntu. Also, I'm using the Beryl window manager, but firefox was already crashing before I installed Beryl. Any suggestions?

Unrelated question: my GRUB menu at startup now has 2 different options for Linux. One of them is Ubuntu ___.15, and the other is __.16. (don't quote me on that, but I do know that the numbers are definitely different). Is this a result of normal upgrades?

Check your CPU usage.

---

