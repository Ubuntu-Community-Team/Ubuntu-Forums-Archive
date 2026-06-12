---
title: "Xubuntu slow startup, is lightdm the culprit?"
date: 2014-07-05
forum: General Help
---

### Post by dentaku65 on 2014-07-05
Hi,

in Xubuntu 14.10 I have this issue on login (autologin); the issue is that from plymouth to the xfce desktop the system takes around 2 minutes to be usable.

I've removed *$HOME$/.cache* and  *$HOME$/.xfce4* but without success; the login process takes always ages. I do not have paticular application at startup.

Digging the logs around my box I see this one from lightdm
```
sudo more /var/log/lightdm/lightdm.log 
```
> [+0.01s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.01s] DEBUG: Starting Light Display Manager 1.10.1, UID=0 PID=1006
[+0.01s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.01s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.01s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.01s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.01s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.01s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.01s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-xubuntu.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Registered seat module unity
[+0.01s] DEBUG: Registered seat module surfaceflinger
[+0.02s] DEBUG: Adding default seat
[+0.02s] DEBUG: Seat: Starting
[+0.02s] DEBUG: Seat: Creating user session
[+0.41s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.41s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.86s] DEBUG: Seat: Creating display server of type x
[+0.87s] DEBUG: Deactivating Plymouth
[+0.90s] DEBUG: Using VT 7
[+0.90s] DEBUG: Seat: Starting local X display on VT 7
[+0.90s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.90s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.90s] DEBUG: DisplayServer x-0: Launching X Server
[+0.90s] DEBUG: Launching process 1057: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.90s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.90s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.90s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+17.06s] DEBUG: Got signal 10 from process 1057
[+17.06s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+17.06s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+17.07s] DEBUG: Quitting Plymouth; retaining splash
[+17.10s] DEBUG: Seat: Display server ready, starting session authentication
[+17.11s] DEBUG: Session pid=1274: Started with service 'lightdm-autologin', username 'sava'
[+17.40s] DEBUG: Session pid=1274: Authentication complete with return value 0: Success
[+17.40s] DEBUG: Seat: Session authenticated, running command
[+17.40s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+17.40s] DEBUG: Session pid=1274: Running command /usr/sbin/lightdm-session startxfce4
[+17.40s] DEBUG: Creating shared data directory /var/lib/lightdm-data/sava
[+17.40s] DEBUG: Session pid=1274: Logging to .xsession-errors
[+17.53s] DEBUG: Activating VT 7
[+17.53s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+19.51s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+48.23s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+66.07s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+74.51s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+135.02s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
As you can see at the end there is this quite amazing waiting time:
> [+17.53s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+19.51s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+48.23s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+66.07s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+74.51s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+135.02s] DEBUG: User /org/freedesktop/Accounts/User1000 change
Do someone have idea what is the correlation between lightdm and freedesktop accounts, and why this activation takes such long time?

TIA
Den

---

### Post by Toz on 2014-07-05
*Moved to **Ubuntu Development Version***

---

### Post by dentaku65 on 2014-07-05
Hi Toz,

why my tread has been moved here? I've stated Xubuntu 14.10 as version not Unicorn

br

---

### Post by Iowan on 2014-07-05
Current version is 14.04, 14.10 releases in October.

---

### Post by grahammechanical on 2014-07-05
Don't take me for an expert the correlation is between this

> [COLOR=#000000]*[+17.10s] DEBUG: Seat: Display server ready, starting session authentication*[/COLOR]
[COLOR=#000000]*[+17.11s] DEBUG: Session pid=1274: Started with service 'lightdm-autologin', username 'sava'*[/COLOR]
[COLOR=#000000]*[+17.40s] DEBUG: Session pid=1274: Authentication complete with return value 0: Success*[/COLOR]

this

> [COLOR=#000000]*+17.40s] DEBUG: Seat: Session authenticated, running command*[/COLOR]
[COLOR=#000000]*[+17.40s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0*[/COLOR]
[COLOR=#000000]*[+17.40s] DEBUG: Session pid=1274: Running command /usr/sbin/lightdm-session startxfce4*[/COLOR]

and this

> [COLOR=#000000]*[+17.53s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1*[/COLOR]
[COLOR=#000000]*[+19.51s] DEBUG: User /org/freedesktop/Accounts/User1000 changed*[/COLOR]

Light Display Manager is handing over control to software elements provided through the freedesktop organisation.

> [COLOR=#000000][FONT=Times New Roman]freedesktop.org is building a base platform for desktop software on Linux and UNIX. The elements of this platform have become the backend for higher-level application-visible APIs such as Qt, GTK+, XUL, VCL, WINE, GNOME, and KDE. [/FONT][/COLOR]

[http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/)

This is some of the stuff that we have compliments of the Freedesktop organisation.

[http://www.freedesktop.org/wiki/Software/](http://www.freedesktop.org/wiki/Software/)

I expect the development branch to be slow on loading, especially as I update every day and a reboot will be reading changed scripts first the first time. I do not think that reducing the loading time is high on the list of priorities at this stage of the development cycle.

By having autologin you cannot know how long it takes to load the desktop environment. You cannot compare the time taken to get to the login screen and the time taken to load the desktop. You cannot identify which side of the login is taking more time than it should.

Regards

---

### Post by dentaku65 on 2014-07-05
> **Iowan said:**
> Current version is 14.04, 14.10 releases in October.

...ops my big fail... I was intended 14.04 :redface:

---

### Post by Toz on 2014-07-05
> **dentaku65 said:**
> ...ops my big fail... I was intendig 14.04 :redface:
*Okay, moving back to **General Help** (I believe thats where it was initally).*

---

### Post by eev2 on 2014-09-06
Hi [**[COLOR=#000000]dentaku65[/COLOR]**]("http://ubuntuforums.org/member.php?u=48938"). I noticed the same problem on my xubuntu 14.04. Did you manage to sort this out?

---

