---
title: "canot log in to Gnome help me!!"
date: 2008-01-14
forum: General Help
---

### Post by keiffee30 on 2008-01-14
i have tried (and failed) to setup my ATI 9200 video card. I have tried other cards but to no avail. I got my system back to a 800x600 16bit, and at 2:00 this morning and had to go to sleep so i turned off the PC. 

When i tried to log in to it i get the login page (GUI) its starts to load into Gnome AND....and then back to a log in (GUI). I have tried running a reconfig of the xorg.conf but that has done nothing.

I did take a backup copy of the xorg.conf before i started, and i used nano to replace this and still not being about to login. 

im now thinking that this might not be the problem (yes im slow). Can some one give me another push in a direction again?

---

### Post by taurus on 2008-01-14
If it dumps you right back out to GUI login screen, one possibilities is no disk space left on / (or more specially, /tmp).  Press <Ctrl><Alt>F2 and login with your username and password.  Then, check out your disk space.

```
df -h
```

---

### Post by keiffee30 on 2008-01-14
thanks for the reply, i have looked at this and its not disk space. 

The fullest drive is only 70%

Is there anything else ?

---

### Post by taurus on 2008-01-14
Look in ~/.xsession-errors to see what's wrong with it.

```
tail -20 ~/.xsession-errors
```

---

### Post by keiffee30 on 2008-01-14
i did this and got.......

alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)
alarm_queue.c:1832 (check_midnight_refresh)

---

### Post by keiffee30 on 2008-01-16
is there anything  else i can do

---

