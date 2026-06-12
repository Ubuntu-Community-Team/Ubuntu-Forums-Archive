---
title: "ssh login problem &quot;xinit: connection to X server lost&quot;"
date: 2016-08-23
forum: General Help
---

### Post by raging hormones on 2016-08-23
logging into my htpc via ssh was fine now I get 
```

X.Org X Server 1.18.3
Release Date: 2016-04-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-92-generic i686 Ubuntu
Current Operating System: Linux htpc 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:28 UTC 2016 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=2e591644-8d18-4225-921b-d1396db87a95 ro splash
Build Date: 22 July 2016  07:50:53AM
xorg-server 2:1.18.3-1ubuntu2.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Aug 22 23:58:47 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

^Cxinit: connection to X server lost

waiting for X server to shut down /usr/bin/xterm: fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":1"
(II) Server terminated successfully (0). Closing log file.

xinit: unexpected signal 2
Couldn't get a file descriptor referring to the console 
```

I'm using openbox and the only thing I've changed since it stopped working was logging with startx openbox-session instead of startx openbox.  Any ideas?

---

### Post by raging hormones on 2016-08-24
I figured it out, I had kodi in the openbox autostart so every time I logged in it started and the x server crashed.  I need to put this in init.

---

