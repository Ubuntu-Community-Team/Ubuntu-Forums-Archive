---
title: "rtorrent on startup?"
date: 2007-01-16
forum: General Help
---

### Post by underdog5004 on 2007-01-16
I'm running rtorrent on an ubuntu 6.10 server through a ssh connection. How can I automate rtorrent so that it automatically runs on start up?

---

### Post by neilp85 on 2007-02-04
rc2 is the defualt run level that ubnut uses so add the following line to /etc/rc2.d/S99rc.local
```
rtorrent
```

---

### Post by neilp85 on 2007-02-04
You probably also want to the following to your ~/.rtorrent.rc file so it resumes your sessions when rtorrent starts
```
session = ~/.session
```

---

### Post by konsole on 2007-02-06
> **neilp85 said:**
> rc2 is the defualt run level that ubnut uses so add the following line to /etc/rc2.d/S99rc.local
```
rtorrent
```

The above will run it as root! ...not a good idea.

Try something like this in /etc/rc.local:

```
su user -c "cd /home/user/torrents; screen -dmS torrents rtorrent"
```

There must be an even better way than this but **DO NOT run it as root**.

---

### Post by SaGa59 on 2007-02-07
1: Install screen (apt-get install screen)

2: login with normal user

crontab -e

write to personal crontab:

@reboot /usr/bin/screen -d -m /usr/bin/rtorrent

ESC :wq ENTER


If reboot the computer, screen will start with rtorrent

If You login with normal user, type in terminal: screen -d -r
Voila...

Warning: if You start the rtorrent in screen from personal crontab, the stop of rtorrent only possible with "kill -2 PID of rtorrent" command.

kill -2 = Ctrl-q in rtorrent console. In the rtorrent, when running in crontab started screen, not work the ctrl-q. In the normal started screen, working.

(sorry for poor english!).

-- 

SaGa

---

### Post by konsole on 2007-02-08
> **SaGa59 said:**
> 1: Install screen (apt-get install screen)

2: login with normal user

crontab -e

write to personal crontab:

@reboot /usr/bin/screen -d -m /usr/bin/rtorrent

ESC :wq ENTER


If reboot the computer, screen will start with rtorrent

If You login with normal user, type in terminal: screen -d -r
Voila...

Warning: if You start the rtorrent in screen from personal crontab, the stop of rtorrent only possible with "kill -2 PID of rtorrent" command.

kill -2 = Ctrl-q in rtorrent console. In the rtorrent, when running in crontab started screen, not work the ctrl-q. In the normal started screen, working.

(sorry for poor english!).

-- 

SaGa

This is no improvement IMO. 

Ideally the OP needs a sysv rc file that handles run levels properly with the ability to start, stop, status etc.

underdog5004 you might want to search the net for a script that you can modify or post in a scripting forum like linuxforums to achieve what you need.

---

### Post by lamego on 2007-02-08
> Ideally the OP needs a sysv rc file that handles run levels properly with the ability to start, stop, status etc.
It is an improvement on the context that rtorrent is not just a service and you may need to interact with it using its own console for which using "screen" is very usefull.

---

### Post by konsole on 2007-02-08
> **lamego said:**
> It is an improvement on the context that rtorrent is not just a service and you may need to interact with it using its own console for which using "screen" is very usefull.

...and did you bother reading my original reply? Does exactly the same thing!

---

### Post by fuhrysteve on 2008-03-31
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup)

---

### Post by toaster.waffle on 2008-05-12
I'm looking for a way to start programs on startup as well (rtorrent and irssi), and found this thread while trying to verify the use of rc.local for this.

> 
# This is a good place to load any misc programs
# on startup (use &>/dev/null to hide output)
su *user* -c "screen -d -m rtorrent"
su *user* -c "screen -d -m irssi"


But a point was raised...

> Ideally the OP needs a sysv rc file that handles run levels properly with the ability to start, stop, status etc.

If these screen sessions are started at boot, will the kernel gracefully kill them on shutdown without start/stop/status/etc?

---

