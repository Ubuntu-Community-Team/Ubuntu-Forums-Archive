---
title: "[SOLVED] upstart not honoring files in /etc/event.d/ after upgrade to feisty"
date: 2007-05-31
forum: General Help
---

### Post by centyx on 2007-05-31
I have the following files in /etc/event.d/

ttyS0, ttyS1, svscan 

which start various services in all multiuser "runlevels." 

Since I upgraded to Feisty, none of these files are being executed. 

I did notice that during the upgrade, ubuntu-minimal was removed due to an upgrade of syslog-ng. I have since 'aptitude install ubuntu-minimal' to remedy this. However, this did not solve the problem with the files in /etc/event.d/.

Here is the contents of one of the files:

```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on shutdown

respawn /sbin/getty 115200 ttyS0

```

Any help greatly appreciated! 

- Michael

---

### Post by centyx on 2007-05-31
Evidently the syntax has changed somewhat.

I copied the syntax in /etc/event.d/tty1.dpkg-dist and now it works.

My /etc/event.d/ttyS0 now reads as follows:

```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0

respawn
exec /sbin/getty 115200 ttyS0

```

Hope this helps someone else.

---

