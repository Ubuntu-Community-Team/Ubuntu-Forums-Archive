---
title: "can't log in after installing kde4"
date: 2008-01-13
forum: General Help
---

### Post by TeeAhr1 on 2008-01-13
Hey, I just installed KDE 4, as directed [here]("http://kubuntu.org/announcements/kde-4.0.php"), and it seemed to go fine, after running apt-get some kde4 applications appeared in the menu, all was good.  I logged out, and now when I come to log in again, I get "A critical error occurred.  Please look at KDM's logfiles(s) for more information" when trying to login to KDE3 or 4.  And to top it off, I don't seem to have any other terminals - Ctrl-Alt-F(1-6) put my monitor to sleep.  I've tried searching around to see if this is a widespread problem, but I can't seem to come up with anything about it... What to do, what to do?

-pd-

EDIT: Forgot the link

EDIT 2: Here's my kdm.log:

```
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux no2pencil 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 13 22:25:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux no2pencil 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 13 22:39:33 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
Link points to "/var/tmp/kdecache-root"
kdmgreet: Fatal IO error: client killed
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux no2pencil 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 13 22:40:21 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux no2pencil 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 13 22:42:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
kdmgreet: Fatal IO error: client killed
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
```
I see the xorg errors in there, I'm not sure what they mean, though.  I checked to see if something had changed my xorg.conf file, but it hasn't changed since Dec. 24.  (What I was doing twiddling with xorg on christmas eve I'm not entirely sure...)

---

### Post by shivathreya on 2008-01-14
I too get this same error. So I am sticking to KDM 3

Shiva

---

### Post by stinger30au on 2008-01-14
to install kde on my ubuntu install i did this

sudo apt-get install kde

saved me plety of d/l rather then get the kde-desktop

---

### Post by TeeAhr1 on 2008-01-14
/bump

---

### Post by TeeAhr1 on 2008-01-14
Joy!  I booted to recovery mode, ran "dpkg-reconfigure kdm" and set kdm as my default login manager (I set it to kdm4) and I'm back in business!  Thx to stdin from #kubuntu for the help!  At the moment, however, I still don't have any other terminals.  Further updates as events warrant.

---

