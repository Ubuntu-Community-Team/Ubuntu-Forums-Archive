---
title: "After xinerama setup login not valid?"
date: 2007-02-05
forum: General Help
---

### Post by Bear Knuckle on 2007-02-05
Hi,

I set up my two monitors using "nvidia-settings". I try to set them up to use an x-server per monitor. The result is quite like this one described here: [Dual Monitor Support With Xinerama HowTo](http://www.ubuntuforums.org/showthread.php?p=1773624).

There seems to be no problem with the setup, the x-server starts and awaits the login.

The last point is the problem, because login is not possible. I enter a valid username/password combination and the feedback is "Wrong username/password".

If I don't use the xinerama setup, the logins work fine, but with two x-servers login with valid users is not possible.

Where can I start to search for a solution? I haven't found anyone in this forums or with a quick search on google having the same problem...

I have the feeling this is some security issue, but I don't know where to start...

**edit:** Now I found this message in the logs, if I try to login with two running x-servers:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux stanislaw 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb  6 10:43:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
**error opening security policy file /usr/lib/xserver/SecurityPolicy**
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
```

There is no such SecurityPolicy. Anyone knows how I have to setup this policy?

---

### Post by daou on 2007-02-06
Since you have already installed the nvidia drivers, you might want to consider running TwinView instead of Xinerama. Have a look at NVIDIA's linux manuals for how to do this. TwinView is a lot more efficient and you will run into less problems with it than with Xinerama.

---

### Post by Bear Knuckle on 2007-02-06
> **daou said:**
> Since you have already installed the nvidia drivers, you might want to consider running TwinView instead of Xinerama. Have a look at NVIDIA's linux manuals for how to do this. TwinView is a lot more efficient and you will run into less problems with it than with Xinerama.
Thank you for this hint. I already ran into TwinView and got it running with a beryl setup. Beryl and Xinerama wouldn't have worked anyway.

I solved the original problem by creating a xorg.con manually and not with nvidia-settings.

---

