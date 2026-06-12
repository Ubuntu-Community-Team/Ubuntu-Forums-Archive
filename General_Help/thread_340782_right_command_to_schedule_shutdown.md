---
title: "right command to schedule shutdown"
date: 2007-01-17
forum: General Help
---

### Post by Sjoerd Mulder on 2007-01-17
Hi all,

I am trying to find a way to schedule an automated shutdown at one o'clock every night. I tried using cron with the command 'shutdown -P' or 'shutdown -h' which did not work. Then I tried to enter 'shutdown -P 01:00' at System-> Preferences-> Sessions -> Startup Programs. That did not do the trick either. If I enter it at a command prompt however, it works fine.

How can I make it work?

Thanks in advance,

Sjoerd Mulder

---

### Post by LotsOfPhil on 2007-01-17
When you tried it with cron, did you run it with root privileges?

Try 'sudo crontab -e' and then put in the shutdown command.

---

### Post by dcstar on 2007-01-17
> **Sjoerd Mulder said:**
> Hi all,

I am trying to find a way to schedule an automated shutdown at one o'clock every night. I tried using cron with the command 'shutdown -P' or 'shutdown -h' which did not work. Then I tried to enter 'shutdown -P 01:00' at System-> Preferences-> Sessions -> Startup Programs. That did not do the trick either. If I enter it at a command prompt however, it works fine.

How can I make it work?

Thanks in advance,

Sjoerd Mulder

All cron commands must have **the full path** to the binary/script.

Find it with:
```
whereis [command]
```

---

### Post by Sjoerd Mulder on 2007-01-17
Thanks for your answers. Still no luck.

I did: 
```
sudo crontab -e
```

and entered
```
05 01 * * * /sbin/shutdown -P
```
to have my pc shutdown at five minutes past one o'clock.
It does not work...

Other suggestions?

---

### Post by rocknrolf77 on 2007-01-17
Maybe kshutdown or wmshutdown can help you? Or maybe you like the cli way better?

---

### Post by ynnhoj on 2007-01-17
the shutdown command needs a time; for example, if i typed in *shutdown -h* into my terminal right now, i'd get:
```
[root@littlemac john]# shutdown -h
Usage:	  shutdown [-akrhHPfnc] [-t secs] time [warning message]
		  -a:      use /etc/shutdown.allow
		  -k:      don't really shutdown, only warn.
		  -r:      reboot after shutdown.
		  -h:      halt after shutdown.
		  -P:      halt action is to turn off power.
		  -H:      halt action is to just halt.
		  -f:      do a 'fast' reboot (skip fsck).
		  -F:      Force fsck on reboot.
		  -n:      do not go through "init" but go down real fast.
		  -c:      cancel a running shutdown.
		  -t secs: delay between warning and kill signal.
		  ** the "time" argument is mandatory! (try "now") **
```

but if i do *shutdown -h **now***, then it will shutdown.

---

### Post by Rippey on 2007-01-17
> **Sjoerd Mulder said:**
> Thanks for your answers. Still no luck.

I did: 
```
sudo crontab -e
```

and entered
```
05 01 * * * /sbin/shutdown -P
```
to have my pc shutdown at five minutes past one o'clock.
It does not work...

Other suggestions?

maybe ```
/sbin/shutdown -P now
``` works

---

### Post by Sjoerd Mulder on 2007-01-17
Hmm, I tried to use wmshutdown but it seems to need 'user-intervention' by clicking on an icon which I don't want: I want to force a shutdown without the need of any user-intervention.  

Kshutdown is said to not work with gnome which I use...

Anybody other suggestions, or suggestions to why the cron thing does not work?

---

### Post by ynnhoj on 2007-01-17
are you sure it's a problem with cron, and not the way you're using the shutdown command?  look at what Rippey, or i, suggested (add "now" to the end of your shutdown thing - '05 01 * * * /sbin/shutdown -P now').

---

### Post by Sjoerd Mulder on 2007-01-17
Sorry, missed both posts. That did it! Thanks!

Now I would like to display a message in gnome, saying that the system will shutdown in 5 minutes. So I would have to issue a command via cron like
```
00 01 * * * (command to give a warning in gnome)
```

Is there a command like that?

---

### Post by jotape99 on 2007-01-22
what about use a zenity script ?

---

### Post by Sjoerd Mulder on 2007-01-23
You are right, I played with it and now have:

```

20 01 * * * /usr/bin/zenity --notification --title "Warning" --text "10 minutes to shutdown"
25 01 * * * /usr/bin/zenity --warning --title "Pas op" --text "5 minutes..."
29 01 * * * /usr/bin/zenity --warning --title "Pas op" --text "1 minute ..."
30 01 * * * /sbin/shutdown -P now

```

Ten minutes before shutdown, a notification icon pops up in the taskbar, then a popupscreen and finally it shuts down.

Great!

---

