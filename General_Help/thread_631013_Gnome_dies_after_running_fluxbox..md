---
title: "Gnome dies after running fluxbox."
date: 2007-12-04
forum: General Help
---

### Post by doctapeppa on 2007-12-04
Hello, 

I installed fluxbox via aptitude, set up the menus and it seemed to work fine, when I go back to my gnome session, however (via gdm), gnome is gone. all I have is an X-shaped cursor. I alt-ctr-bkspc out of there and try logging into gnome failsafe and nothing. only  blank orange screen with an arrow pointer but no bars or anything else. If I go back to flux box it seems to be working but I can't open up a gnome terminal.  If I reboot the system all this is fixed. If I try switch to flux or (blackbox for that matter) and go back to gnome the same thing happens again. 

what appears to be a relevant entry in syslog is this:

```
Dec  3 23:39:58 ubuntu gdm[4986]: WARNING: gdm_auth_user_add: /home/frank/.Xauthority is not owned by uid 1000. 
```

I checked .Xauthority but I don't know what that's supposed to look like, I haven't messed with it.

```
~$ ls -l .Xauthority
-rw------- 1 root root 271 2007-12-03 20:58 .Xauthority
```

please help! :confused:

---

### Post by -grubby on 2007-12-04
the only thing I can think of is typing ```
sudo update-menus 
``` in a terminal, or maybe reinstalling GDM 

```
sudo apt-get remove gdm
```

```
sudo apt-get install gdm
```

---

### Post by djbuzzkill on 2008-07-18
this happened to me as well.  Was there any resolution to this, doctapeppa?

---

