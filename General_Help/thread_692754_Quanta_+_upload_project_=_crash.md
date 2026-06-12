---
title: "Quanta + upload project = crash"
date: 2008-02-10
forum: General Help
---

### Post by edkirin on 2008-02-10
I'm using Quanta+ v3.5.8 in my Kubuntu v7.10 for web development and it all worked fine since kernel upgrade to 2.6.22-14. Now, when I'm trying to upload project to web server using Project / Upload project, everything crashes and X server logs out to log-in screen.

All I see in syslog is

Feb  9 23:21:23 sunce kdm[9517]: X server for display :0 terminated unexpectedly

Any suggestions? How to locate the problem?

---

### Post by edkirin on 2008-02-10
I checked other log files and I found following:

kdm.log:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux sunce 2.6.22-14-386 #1 Fri Feb 1 04:32:03 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 10 10:36:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/bin/X(ProcPolyPoint+0xff) [0x808c5af]
3: /usr/bin/X [0x81576c1]
4: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
5: /usr/bin/X(main+0x495) [0x8076f05]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d4c050]
7: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

```

Maybe this helps.

---

### Post by eZoulou on 2008-03-28
I have the same here. Upload did work once but I cannot reproduce the succesfull sequence of actions. Now, it systematicaly crashes on file upload... 
Did you find a solution to this situation? 
florent/.

---

### Post by edkirin on 2008-03-29
Unfortunately, I haven't. But, recently I made a fresh install of Ubuntu v7.10 and Quanta project upload now works ok. However, it still has some strange issues: upload window freezes and I need just to resize it a bit to unfreeze it. After this, upload works.

---

### Post by eZoulou on 2008-04-01
In fact I have a solution for the upload crash : use drag and drop instead of right clic. 
It works for me, on hardy (ubuntu 8.04). 
The upload freezing happened to me also, when I was on gutsy 7.10. I had to kill the process though! 
Anyway, I have just discovered Aptana and will give it a try today! It looks great!

---

