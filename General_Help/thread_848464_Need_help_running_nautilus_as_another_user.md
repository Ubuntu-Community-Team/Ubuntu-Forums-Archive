---
title: "Need help running nautilus as another user"
date: 2008-07-03
forum: General Help
---

### Post by RangoTheClown on 2008-07-03
I have the latest version of ubuntu.  I am trying to run nautilus as another user, called altuser, which is an administrator like my main account, which I will call mainuser for the purpose of these forums.  I log on directly as main user, but I want to run nautilus as altuser.  I have tried using su, sudo, gksu, and gksudo, and I always get the same error.  It says that it can't open the display.

Here is what I have tried:

su altuser
nautilus (once I have switched to altuser)

sudo -u altuser nautilus

gksu -u altuser nautilus

gksudo -u altuser nautilus

Each of these commands gives me the same error message:
"cannot open display: 
Run 'nautilus --help' to see a full list of available command line options."

However, I have no problem running nautilus as root, although I do not wish to do this here in order to avoid deleting important system files.  Any help on this would be appreciated.

---

### Post by avtolle on 2008-07-03
I think you will need to log on as altuser to accomplish whatever it is you are trying to accomplish.

---

### Post by aysiu on 2008-07-03
I hope you find a solution, but if you don't, a workaround would be installing *xnest* and then running ```
gdmflexiserver --xnest
``` and logging in temporarily as that user in a window inside your session.

---

### Post by RangoTheClown on 2008-07-03
> **aysiu said:**
> I hope you find a solution, but if you don't, a workaround would be installing *xnest* and then running ```
gdmflexiserver --xnest
``` and logging in temporarily as that user in a window inside your session.

I have done that.  It will suffice if need be.  I was simply wondering if I could just run nautilus as this other user.  Thank you, though.

---

### Post by nicholas.alipaz on 2012-09-09
This worked for me:
```

$ xhost +SI:localuser:usernameyouwanttorunas
$ sudo su - usernameyouwanttorunas
$ nautilus

```
Taken from [http://ubuntuforums.org/showthread.php?p=10418202#post10418202](http://ubuntuforums.org/showthread.php?p=10418202#post10418202)

Hope that helps someone else as well.

---

### Post by wildmanne39 on 2012-09-09
Thanks for sharing. Thread Closed.

---

