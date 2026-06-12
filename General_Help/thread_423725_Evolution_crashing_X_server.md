---
title: "Evolution crashing X server"
date: 2007-04-26
forum: General Help
---

### Post by chrisccoulson on 2007-04-26
I've switched on my machine this morning  as normal this morning, but when I fire up Evolution, X crashes and sends me back to the login screen. This happens consistently within a second or so of opening Evolution. The messages logged in /var/log/syslog are:

```
Apr 26 10:16:58 localhost gdm[9683]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

At the bottom of /var/log/Xorg.0.log.old I can see:

```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b03d12e5d40]
2: /usr/X11R6/bin/X(miRegionDestroy+0x4) [0x4d7384]
3: /usr/X11R6/bin/X(miSetShape+0x2a8) [0x4e2308]
4: /usr/X11R6/bin/X [0x4ec4e7]
5: /usr/X11R6/bin/X [0x4ec8ca]
6: /usr/X11R6/bin/X(Dispatch+0x1cb) [0x44df4b]
7: /usr/X11R6/bin/X(main+0x45d) [0x43703d]
8: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b03d12d28e4]
9: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting
```

This is on an up-to-date Feisty install. I did install some updates yesterday which I noticed this morning came back from backports and proposed, so I've downgraded those this morning. This has made no difference. Those packages were apport, apport-gtk, gnome-control-centre, libgnome-window-settings1, update-manager-core, capplets-data, libslab0, python-problem-report, python-launchpad-bugs, python-apport, rdesktop and update-manager.

Is anyone else having a similar problem?

---

### Post by bapoumba on 2007-04-26
> **chrisccoulson said:**
> 

This is on an up-to-date Feisty install. I did install some updates yesterday which I noticed this morning came back from backports and **proposed**
Hi,
not sure I can help you troubleshooting this, but:

1- feisty up to date without backports and proposed: no problem here.
2- -proposed repositories are designed to test packages before they hit the main repos. You should check LP for bugs or file a bug.

---

### Post by bapoumba on 2007-04-26
> **bapoumba said:**
> Hi,
not sure I can help you troubleshooting this, but:

1- feisty up to date without backports and proposed: no problem here.
2- -proposed repositories are designed to test packages before they hit the main repos. You should check LP for bugs or file a bug.

Edit: googling around shows it may be an issue with video drivers. Could you try with vesa drivers for ex, if you are currently using proprietary ones?

---

### Post by chrisccoulson on 2007-04-26
I've actually just narrowed it down to mail-notification. If I kill the mail-notification process and then start Evolution, it works fine. If I open up Evolution with mail-notification running, and then I receive new mail, the X Server crashes.

I'll dig a bit further and see if this is related to graphics drivers, but it does seem that it isn't really related to Evolution.

---

