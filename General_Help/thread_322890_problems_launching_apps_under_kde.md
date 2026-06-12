---
title: "problems launching apps under kde"
date: 2006-12-21
forum: General Help
---

### Post by thePuck on 2006-12-21
I got a problem in kde where I launch an app and it just hangs there for a while then the indicator disappears...doesn't happen every time I launch something, but an awful lot...anyone heard of this or got a solution?

It happens under kubuntu, a server install with kde-core, and a server install with kde.

Thanks.

---

### Post by po0f on 2006-12-21
thePuck,

Can you try running the app from Konsole?  Maybe this will shed more light.  Open up Konsole (if it will load  :)) and just start a KDE app:
```
[FONT="Courier New"]$ konqueror[/FONT]
```

---

### Post by thePuck on 2006-12-21
Interestingly, I can't get it to happen from the command line. For example, I use synaptic (like it better than adept). If I call synaptic from the kde menu, about half the time it starts to open, indicator cursor bounces and the taskbar shows it launching. After about 30 secs - a minute it just vanishes. If I call synaptic from the command line it always launches (or after about 10 tries it didn't hang). Huh.

I checked what command the menu uses to launch it, and it is just plain "synaptic". Both "synaptic" and "sudo synaptic" work just fine from the command line.

Something wrong with kicker then?

---

### Post by thePuck on 2006-12-21
okay with kdesu kate I get kdesu (kdelibs): WARNING: [/build/buildd/kdelibs-3.5.5/./kdesu/stub.cpp:166] Unknown request: --><--

sudo kate I get

DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5278' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

this all worked before I installed driver. Could this be the new ATI driver or prelinking or what?

---

