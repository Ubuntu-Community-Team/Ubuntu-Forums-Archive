---
title: "gapcmon won't load"
date: 2014-04-30
forum: General Help
---

### Post by tkinzey on 2014-04-30
I just installed gapcmon to monitor my ups, but now it won't load.  I type /usr/bin/gapcmon on the command line, and it just hangs.  I tried dl'ing the .deb, and also tried compiling from the .bz2 file.  Ubuntu 12.04 LTS, and gapcmon 0.8.9.  Any idea on how to fix this?  It was working, then I tried to get the tray icon to load, now I can't get it to open at all.  Any info needed on my setup, please let me know.

Thanks

---

### Post by tgalati4 on 2014-04-30
Are you running the *apcupsd* server?

```
ps aux | grep apcupsd
```

Are you getting apcups log files in /var/log?

Try a different monitor such as *nut-monitor*.

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

---

### Post by tkinzey on 2014-04-30
root     11262  0.0  0.0  37656   916 ?        Ssl  21:18   0:01 /sbin/apcupsd
myuseridhere 12746  0.0  0.0   4388   832 pts/0    S+   21:49   0:00 grep --color=auto apcupsd

that shows I am no?

O, and when I try nut-monitor, it loads but does not show my ups.  It has "error connecting to local host, errno 111, connection refused".

---

### Post by tkinzey on 2014-04-30
in /var/log apcupsd.events I have this:

2014-04-30 15:00:59 -0400  Valid lock file for pid=1985, but not ours pid=8842
2014-04-30 15:00:59 -0400  apcupsd FATAL ERROR in apcupsd.c at line 285
Failed to acquire device lock file
2014-04-30 15:00:59 -0400  Valid lock file for pid=1985, but not ours pid=8842
2014-04-30 15:00:59 -0400  apcupsd error shutdown completed
2014-04-30 15:01:03 -0400  Valid lock file for pid=1985, but not ours pid=8864
2014-04-30 15:01:03 -0400  apcupsd FATAL ERROR in apcupsd.c at line 285
Failed to acquire device lock file
2014-04-30 15:01:03 -0400  Valid lock file for pid=1985, but not ours pid=8864
2014-04-30 15:01:03 -0400  apcupsd error shutdown completed
2014-04-30 15:15:27 -0400  Valid lock file for pid=1985, but not ours pid=20359
2014-04-30 15:15:27 -0400  apcupsd FATAL ERROR in apcupsd.c at line 285
Failed to acquire device lock file
2014-04-30 15:15:27 -0400  Valid lock file for pid=1985, but not ours pid=20359
2014-04-30 15:15:27 -0400  apcupsd error shutdown completed
2014-04-30 15:15:32 -0400  Valid lock file for pid=1985, but not ours pid=20363

there's more of lines like those

---

### Post by tkinzey on 2014-04-30
When I run apcaccess status, I get all the info, so that works fine, just for whatever reason gapcmon won't load to display that info.  Either from opening it via CLI, /usr/bin/gapcmon, or clicking the APCUPSD Monitor icon from dash, the system tray icon? (pardon my terminology, *nix noob here), is a yellow background with little items in it.  When I clcik it, the yellow background changes to black, to yellow, black..etc, almost as if its blinking.  Would that help diagnose?  As I said, via terminal/cli, I type /usr/bin/gapcmon, and the term hangs, i.e., does not get me back to a prompt.

---

### Post by tgalati4 on 2014-05-01
The events log file is telling you what is happening.  There is a lock file that needs to be deleted so that the apcupsd server can operate properly.  Stop the server, delete the lock file, restart the server:

```
sudo service apcupsd stop
```

Look for the lock file--probably in /var/run.  The purpose of the lock file is to prevent two instances of the ups server from running.  If the server isn't running, then the monitor won't run either.  The events file should be empty except for daemon start/stops, power outages, or network connection disruptions.

---

### Post by tkinzey on 2014-05-01
Ok, so somebody suggested installing gconf-editor and using that to uncheck the use tray icon option, as that is borked....and that fixed it!  Thanks!

---

