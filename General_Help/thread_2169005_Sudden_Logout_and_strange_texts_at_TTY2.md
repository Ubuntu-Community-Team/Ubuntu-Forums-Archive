---
title: "Sudden Logout and strange texts at TTY2"
date: 2013-08-20
forum: General Help
---

### Post by d2btoo on 2013-08-20
Hello,

I was typing a long post in another forum when suddenly I was logged out and taken to TTY2 (where I able to notice some long strange text briefly) and then to the login-screen.

Once logged in back, I checked the log and found following entries (which seems strange to me):
```

init: tty2 main process ended, respawning
gnome-session[1384]: WARNING: Detected that screensaver has left the bus
acpid: client connected from 3833[0:0]
acpid: 1 client rule loaded
init: tty2 main process ended, respawning
acpid: client 3833[0:0] has disconnected
acpid: client connected from 3833[0:0]
acpid: 1 client rule loaded


```
and in auth log...
```

gnome-keyring-daemon[1366]: dbus failure unregistering from session: Connection is closed
gnome-keyring-daemon[1366]: dbus failure unregistering from session: Connection is closed
polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.28, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en) (disconnected from bus)
gdm-session-worker[3874]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "<me>"
gdm-session-worker[3874]: pam_unix(gdm:session): session opened for user <me> by (uid=0)


```

Then I pressed Ctrl+Alt+F2 to go to TTY2 and find those strange texts still there; see normally when I go to TTY's I see something like this:

```
Ubuntu <version> <host> tty#
<host> login:
```
but this time I saw something like this :
```
Ubuntu <version> <host> tty#
<host> login: !ppppp//****<more text here>
Password:

<host> login: 9xxxxxxk<more text here>
Password:


```

I'm sorry, I forgot to take a screen-shot, but I panicked and rebooted the machine.  :oops: 
So what's going on here.... Can anybody shed some light.... thanks!

---

### Post by VMC on 2013-08-20
There is a similar error [bug report]("https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/1156891") on "[COLOR=#000000][FONT=Ubuntu Mono]screensaver has left the bus". Are you using NFS?[/FONT][/COLOR]

---

### Post by d2btoo on 2013-08-21
Hello,
Thanks for responding, but I'm not using NFS.

In-fact this is the old Lucid box.

---

