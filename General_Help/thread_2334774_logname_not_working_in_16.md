---
title: "logname not working in 16"
date: 2016-08-22
forum: General Help
---

### Post by chopra on 2016-08-22
Not sure if this warrants a bug report or a post here.

When I enter logname into the terminal screen, after having upgraded to 16.04, I get the error message:
logname: no login name.

whoami works, and logname works in xterm and tty1-6, just not in the terminal opened from the desktop.

---

### Post by TheFu on 2016-08-22
Check the difference in environment between the desktop terminal and the xterm.  I suspect the PATH is different, somehow. Don't know why that would be.
```
$ which logname
/usr/bin/logname

```
That is on my 16.04 system, so I'd guess it is a configuration issue on your machine.

---

### Post by chopra on 2016-08-22
which and type give /usr/bin/logname consistently.  In addition, typing the full path name of the executable gives the same results as simply typing logname. I'm not sure what environment variable logname looks at, or I could check it.

---

### Post by steeldriver on 2016-08-22
Hmm... just tried it in a gnome-terminal in 16.04 VM and I get 

```

logname: no login name

```

It seems like gnome-terminal doesn't write pts info to the utmp logfile - see for example [Why do only some terminals get a pts](http://unix.stackexchange.com/a/62813/65304)

---

### Post by TheFu on 2016-08-23
Doesn't help with this issue inside that terminal, but this is another reason why using the full path to programs inside scripts is a best practice.
[http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

BTW, I've never used gnome-terminal.  Prefer straight xterms myself.

---

### Post by vasa1 on 2016-08-23
logname and /usr/bin/logname don't work in lxterminal as well (Lubuntu 16.04).

I also have xfce4-terminal on the same system and logname works in that!

---

### Post by TheFu on 2016-08-23
/usr/bin/logname does work inside an "lxterm" on a 16.04 server with a few GUI tools added (my normal desktop install method). Installed lxterminal  and it failed.

```
$ /usr/bin/logname 
/usr/bin/logname: no login name

```
Interesting.

---

