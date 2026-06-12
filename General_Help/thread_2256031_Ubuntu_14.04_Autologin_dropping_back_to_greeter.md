---
title: "Ubuntu 14.04 Autologin dropping back to greeter"
date: 2014-12-09
forum: General Help
---

### Post by davidduwaer on 2014-12-09
Hey everyone,

I've setup lightdm to auto-login my account and to disable guest login. The disable guest login part is working, but auto-login seems to be not working.

Checking the lightdm.log it seems that auto-login in fact *does* work initially, but something seems to cause my session to end, moving me back to the login screen where I have to log in manually. After logging in manually (with the same account as I do the auto-login on), everything works fine.

This is the log, where I've highlighted the part where it succesfully automatically starts my session and then kills it again.

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.1, UID=0 PID=1155
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/12-autologin.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-autologin.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.15s] DEBUG: Adding default seat
[+0.15s] DEBUG: Seat: Starting
[+0.15s] DEBUG: Seat: Creating user session
[+0.80s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.80s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+1.28s] DEBUG: Seat: Creating display server of type x
[+1.33s] DEBUG: Deactivating Plymouth
[+1.38s] DEBUG: Using VT 7
[+1.38s] DEBUG: Seat: Starting local X display on VT 7
[+1.38s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+1.39s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+1.39s] DEBUG: DisplayServer x-0: Launching X Server
[+1.39s] DEBUG: Launching process 1219: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1.45s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+1.46s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+1.46s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+3.18s] DEBUG: Got signal 10 from process 1219
[+3.18s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+3.18s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+3.18s] DEBUG: Quitting Plymouth; retaining splash
[+3.34s] DEBUG: Seat: Display server ready, starting session authentication
[B][+3.34s] DEBUG: Session pid=1234: Started with service 'lightdm-autologin', username 'david'
[+3.68s] DEBUG: Session pid=1234: Authentication complete with return value 0: Success
[+3.68s] DEBUG: Seat: Session authenticated, running command
[+3.68s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+3.71s] DEBUG: Session pid=1234: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+3.71s] DEBUG: Creating shared data directory /var/lib/lightdm-data/david
[+3.71s] DEBUG: Session pid=1234: Logging to .xsession-errors
[+3.82s] DEBUG: Activating VT 7
[+3.82s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+3.83s] DEBUG: Session pid=1234: Exited with return value 1
[+3.83s] DEBUG: Seat: Session stopped
[+3.83s] DEBUG: Seat: Stopping display server, no sessions require it[/B]
[+3.83s] DEBUG: Sending signal 15 to process 1219
[+4.09s] DEBUG: Process 1219 exited with return value 0
[+4.09s] DEBUG: DisplayServer x-0: X server stopped
[+4.09s] DEBUG: Releasing VT 7
[+4.09s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+4.09s] DEBUG: Seat: Display server stopped
[+4.09s] DEBUG: Seat: Active display server stopped, starting greeter
[+4.09s] DEBUG: Seat: Creating greeter session
[+4.09s] DEBUG: Seat: Creating display server of type x
[+4.09s] DEBUG: Using VT 7
[+4.09s] DEBUG: Seat: Starting local X display on VT 7
[+4.09s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+4.09s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+4.09s] DEBUG: DisplayServer x-0: Launching X Server
[+4.09s] DEBUG: Launching process 1252: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+4.09s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+4.53s] DEBUG: Got signal 10 from process 1252
[+4.53s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+4.53s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+4.54s] DEBUG: Seat: Display server ready, starting session authentication
[+4.54s] DEBUG: Session pid=1256: Started with service 'lightdm-greeter', username 'lightdm'
[+4.63s] DEBUG: Session pid=1256: Authentication complete with return value 0: Success
[+4.63s] DEBUG: Seat: Session authenticated, running command
[+4.63s] DEBUG: Session pid=1256: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+4.66s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+4.66s] DEBUG: Session pid=1256: Logging to /var/log/lightdm/x-0-greeter.log
[+4.73s] DEBUG: Activating VT 7
[+4.73s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c2
[+7.14s] DEBUG: Session pid=1256: Greeter connected version=1.10.1
[+7.50s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+8.80s] DEBUG: Session pid=1256: Greeter start authentication for david
[+8.80s] DEBUG: Session pid=1771: Started with service 'lightdm', username 'david'
[+8.84s] DEBUG: Session pid=1771: Got 1 message(s) from PAM
[+8.86s] DEBUG: Session pid=1256: Prompt greeter with 1 message(s)
[+106.99s] DEBUG: Session pid=1256: Continue authentication
[+112.28s] DEBUG: Session pid=1771: Authentication complete with return value 0: Success
[+112.28s] DEBUG: Session pid=1256: Authenticate result for user david: Success
[+112.28s] DEBUG: Session pid=1256: User david authorized
[+112.28s] DEBUG: Session pid=1256: Greeter requests session ubuntu
[+112.29s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+112.29s] DEBUG: Session pid=1256: Sending SIGTERM
[+112.32s] DEBUG: Session pid=1256: Exited with return value 0
[+112.32s] DEBUG: Seat: Session stopped
[+112.32s] DEBUG: Seat: Greeter stopped, running session
[+112.32s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+112.39s] DEBUG: Session pid=1771: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+112.39s] DEBUG: Creating shared data directory /var/lib/lightdm-data/david
[+112.39s] DEBUG: Session pid=1771: Logging to .xsession-errors
[+113.16s] DEBUG: Activating VT 7
[+113.16s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c3
[+113.82s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+220.56s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
```

What could be the cause of this?

Thanks,

David

---

### Post by davidduwaer on 2014-12-09
Anyone?

---

