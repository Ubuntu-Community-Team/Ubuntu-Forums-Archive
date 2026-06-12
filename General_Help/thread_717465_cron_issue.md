---
title: "cron issue"
date: 2008-03-07
forum: General Help
---

### Post by alexebird on 2008-03-07
I my crontab file setup so that it starts azureus at 2am and then kills it in the morning.  The problem is that when it starts azureus, the window has no border, the UI is different than normal, and the azureus window is on top of every other window.  It still works, but its more annoying to know that something is messed up than anything else.  Any solutions?

Thanks,

Alex

---

### Post by alexebird on 2008-03-07
Heres a picture of whats going on:

[IMG]http://home.wi.rr.com/pbrc/files/messed-up.png[/IMG]

Its hard to tell, but if you look closely you can see that there is no window border.

---

### Post by linuxh8ter on 2008-03-07
cron calls, azureus, which uses the gtk or whatever toolkit it uses. The window borders are managed by gnome or whatever window manager/desktop environment you use. Since cron calls is without going through the window manager, you wont get the border. you should call, the gnome runner command with azureus as an argument, that should solve your  problem.

---

### Post by alexebird on 2008-03-07
Hey thanks a lot for the reply.  I added the grun command before azureus in my crontab file, which is

```
0 2 * * * export DISPLAY=:0 && grun azureus
15 9 * * * ps waux | grep -i bird | grep -i azureus2 | awk '{print $2}' | xargs kill

```

but it still doesnt work.  is grun the right command?

---

### Post by alexebird on 2008-03-10
Just in case someone else out there is having this problem, I fixed it by changing the
```
export DISPLAY=:0
```
part to:
```
export DISPLAY=:1.0
```
where ":1.0" is what is printed by running the command:
```
echo $DISPLAY
```

alex

---

