---
title: "Megasync Problems"
date: 2015-08-01
forum: General Help
---

### Post by GrouchyGaijin on 2015-08-01
I have been using a free account at Mega.nz and today I noticed that when I ran the software updater on Ubuntu 14.04 64 bit I got an error with there was a problem with the Megasync client.

I have tried purging Megasync and I have removed the directory at ```
/home/john/.local/share/data/Mega Limited
```

However when I install the Megasync client I get this error message:
```

Selecting previously unselected package libc-ares2:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 882047 files and directories currently installed.)
Preparing to unpack .../libc-ares2_1.10.0-2_amd64.deb ...
Unpacking libc-ares2:amd64 (1.10.0-2) ...
Selecting previously unselected package libcrypto++9.
Preparing to unpack .../libcrypto++9_5.6.1-6+deb8u1build0.14.04.1_amd64.deb ...
Unpacking libcrypto++9 (5.6.1-6+deb8u1build0.14.04.1) ...
Setting up libc-ares2:amd64 (1.10.0-2) ...
Setting up libcrypto++9 (5.6.1-6+deb8u1build0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Selecting previously unselected package megasync.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 882058 files and directories currently installed.)
Preparing to unpack .../megasync-xUbuntu_14.04_amd64 (1).deb ...
Unpacking megasync (2.1.1) ...
Setting up megasync (2.1.1) ...
dpkg: error processing package megasync (--install):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 megasync

```

If I ignore the error Megasync seems to function, however any time I update the software on the computer I get a message that there were problems with Megasync.

Has anyone had this happen to them and if so how can I fix the problem?

---

### Post by Vladlenin5000 on 2015-08-01
I suggest you obtain the latest .deb from Mega. The sync app was recently updated. It went trough the normal update process and I had no issues.
Trying to install now the old version may give such errors.

---

### Post by GrouchyGaijin on 2015-08-01
The version I downloaded from Mega's website is 2.1.1.  What version are you running?

---

### Post by Vladlenin5000 on 2015-08-01
The same. Had it previously installed with an older one, it got updated and it's fine.
There's something with your system, probably a dependencies problem or other.

---

### Post by GrouchyGaijin on 2015-08-01
[COLOR=#ff0000][B]UPDATE

[/B][/COLOR]If I run the command
```
dpkg --configure -D 777 megasync
```

I get this:

```
Today is Sat Aug 01 @ 15:55:40 ~ $ sudo dpkg --configure -D 777 megasync[sudo] password for john: 
D000001: ensure_diversions: new, (re)loading
D000040: checking dependencies of megasync:amd64 (- <none>)
D000400:   checking group ...
D000400:     checking possibility  -> libc-ares2
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libc6
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libgcc1
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libqt4-dbus
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libqt4-network
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libqtcore4
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libqtgui4
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libsqlite3-0
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libssl1.0.0
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libstdc++6
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> zlib1g
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libcrypto++9
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000040: ok 2 msgs >><<
D000040:     checking Breaks
Setting up megasync (2.1.1) ...
D000002: fork/exec /var/lib/dpkg/info/megasync.postinst ( configure  )
dpkg: error processing package megasync (--configure):
 subprocess installed post-installation script returned error exit status 2
D000001: ensure_diversions: same, skipping
Errors were encountered while processing:
 megasync



```

---

