---
title: "Choqok generating &quot;Invalid interface to SNW_SERVICE&quot; error"
date: 2013-08-03
forum: General Help
---

### Post by felgro on 2013-08-03
Hi,

I have installed via ppa "choqok 1.4 git (twitter 1.1 API)" - version 1.4-2-1git0 - which is to bring it up to speed with the twitter api changes that broke it and most other twitter clients. This is on Ubuntu 12.04 (i386 precise). Running from a terminal generates -

```
Choqok  1.3.1 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QSystemTrayIcon::setVisible: No Icon set
"sni-qt/15426" WARN  12:31:00.142 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
QSystemTrayIcon::setVisible: No Icon set
me@beelz:~$ choqok(15426)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "proxy.desktop" not found
```

It appears to load, and allows you to add accounts but fatally terminates when you attempt to authenticate account -

```
HMAC(SHA1) is not supported!
KCrash: Application 'choqok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/me/.kde/socket-beelz/kdeinit4__0
```

Crash handler: 
```
Executable: choqok PID: 15426 Signal: Aborted (6)
```

The problems -

[LIST]
[*]I can't find any meaningful information on what a SNW_SERVICE error actually is 
[*]The system misidentifies the choqok version 
[*]The immediate culprit seems libc6, >= v2.4 required; installed, and "latest" according to Synaptic, is latest 2.15 for lucid 10.04 (!) 
[/LIST]
My only desire is for a version of Choqok that plays nicely with the new twitter api. Any suggestions? I know I'm not the only choqok user out there - and I can't find any sensible info elsewhere.

---

### Post by felgro on 2013-08-07
Surely I'm not the sole choqok user here? How do others deal with the new twitter api?

---

### Post by oldos2er on 2013-08-07
I had to stop using it, since as you noted even the latest version is not working.

---

