---
title: "Start vino-server from terminal SSH"
date: 2012-11-16
forum: General Help
---

### Post by robinasa on 2012-11-16
Hello,

Im using  ubuntu as a fileserver and i have som trouble with vino-server.
Sometimes it uses 100% of cpu, and i have to kill the session and restart vino-server.

anyway, i have now reistalled vino-server and fill start the vino-server application by the ssh terminal.

What command to use?



Thanks!

---

### Post by Lars Noodén on 2012-11-16
It should be like this:

```

/usr/lib/vino/vino-server &

```

There also might be a way to limit the amount of CPU allowed Vino.  

If Vino causes you too much trouble, you can try other VNC servers like tightvnc-server and x11vnc.

---

### Post by robinasa on 2012-11-16
I got this: 
robin@robin-1000H:~$ /usr/lib/vino/vino-server &
[1] 12176
robin@robin-1000H:~$ Cannot open display: 
Run 'vino-server --help' to see a full list of available command line options

[1]+  Exit 1                  /usr/lib/vino/vino-server
robin@robin-1000H:~$

---

### Post by Lars Noodén on 2012-11-16
Have you tried running 'vino-preferences ' first?  You can set 'Allow others to view your desktop'.

---

### Post by robinasa on 2012-11-16
Yes, all settings are fine

---

### Post by robinasa on 2012-11-16
I got it startet when using sudo in front!

But when i exit terminal the application stops.
And when I type jobs it stands it`s stopped

---

### Post by Lars Noodén on 2012-11-16
It shouldn't be run as root with sudo.  That can make small mistakes into big mistakes.  Try setting the display instead.

```

/usr/lib/vino/vino-server --display=:0.0 &

```

---

### Post by robinasa on 2012-11-16
```
(vino-server:12403): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed

** (vino-server:12403): WARNING **: Command line `dbus-launch --autolaunch=b09053006ca21a04e518ebff0000000d --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
** Message: The desktop sharing service is already running, exiting.


```

What is this meaning?

---

### Post by Lars Noodén on 2012-11-16
It appears that you already have an instance of Vino running.  Try looking for it and killing it.

```

pgrep -l vino-server 
pkill -x vino-server 

```

Then try running it again with the display option.pgrep

---

### Post by robinasa on 2012-11-16
witch is the best command for listing running applications?


Thanks

---

### Post by Lars Noodén on 2012-11-16
[ps](http://manpages.ubuntu.com/manpages/precise/en/man1/ps.1posix.html) or [top](http://manpages.ubuntu.com/manpages/precise/en/man1/top.1.html) can do that.  There are a heck of a lot of options for ps, so read the manual page thoroughly.  You might want to pipe the output through less.

```

ps auw | less

```

Also, there might be some graphical utilities like 'system monitor' that will do the job as well.

---

### Post by robinasa on 2012-11-16
I have Ubuntu KDE by the way... Anyone who can help?

---

