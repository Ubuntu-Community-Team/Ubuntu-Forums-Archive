---
title: "Why lightdm continue to kill X?"
date: 2013-11-05
forum: General Help
---

### Post by gspe on 2013-11-05
This a picture of lightdm greeter taken this morning, as you can see is totally black!!!

[ATTACH=CONFIG]247581[/ATTACH]

Every couple of boot lightdm refuse to start or better it starts but suddenly it kills X so i have no login screen.
The solution is simple, just switch to terminal ctr-alt-F1 and issue the command "sudo service lightdm restart" and the login screen is back.

But this is totally not acceptable!!! The login screen have to work, period.

I've filed a bug report some times ago but this bug is still present

This is lightdm.log
as you can see the process 1178 send a signal 15 so no login screen

```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.8.2, UID=0 PID=1178
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.07s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.07s] DEBUG: Seat: Creating display server of type x
[+0.07s] DEBUG: Seat: Starting local X display
[+0.14s] DEBUG: Quitting Plymouth
[+0.17s] DEBUG: Using VT 7
[+0.17s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.19s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.19s] DEBUG: DisplayServer x-0: Launching X Server
[+0.19s] DEBUG: Launching process 1194: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.19s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.19s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.19s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+3.37s] DEBUG: Got signal 10 from process 1194
[+3.37s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+3.37s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+3.37s] DEBUG: Seat: Display server ready, starting session authentication
[+3.37s] DEBUG: Session: Setting XDG_VTNR=7
[+3.37s] DEBUG: Session pid=1463: Started with service 'lightdm-greeter', username 'lightdm'
[+3.90s] DEBUG: Session pid=1463: Authentication complete with return value 0: Success
[+3.90s] DEBUG: Seat: Session authenticated, running command
[+3.90s] DEBUG: Session pid=1463: Setting XDG_VTNR=7
[+3.90s] DEBUG: Session pid=1463: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+3.91s] DEBUG: Session pid=1463: Logging to /var/log/lightdm/x-0-greeter.log
[+3.97s] DEBUG: Activating VT 7
[+6.46s] DEBUG: Session pid=1463: Greeter connected version=1.8.2
[+8.25s] DEBUG: Session pid=1463: Greeter start authentication for gspe
[+8.25s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+8.25s] DEBUG: Session: Setting XDG_VTNR=7
[+8.25s] DEBUG: Session pid=1816: Started with service 'lightdm', username 'gspe'
[+8.25s] DEBUG: Session pid=1463: Greeter start authentication for gspe
[+8.25s] DEBUG: Session pid=1816: Sending SIGTERM
[+8.25s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+8.25s] DEBUG: Session: Setting XDG_VTNR=7
[+8.25s] DEBUG: Session pid=1817: Started with service 'lightdm', username 'gspe'
[+8.25s] DEBUG: Got signal 15 from process 1178
[+8.25s] DEBUG: Caught Terminated signal, shutting down
[+8.25s] DEBUG: Stopping display manager
[+8.25s] DEBUG: Seat: Stopping
[+8.25s] DEBUG: Seat: Stopping display server
[+8.25s] DEBUG: Sending signal 15 to process 1194
[+8.25s] DEBUG: Seat: Stopping session
[+8.25s] DEBUG: Session pid=1463: Sending SIGTERM
[+8.25s] DEBUG: Seat: Stopping session
[+8.25s] DEBUG: Session pid=1817: Sending SIGTERM
[+8.25s] DEBUG: Session pid=1817: Terminated with signal 15
[+8.25s] DEBUG: Session: Failed during authentication
[+8.25s] DEBUG: Seat: Session stopped
[+8.25s] DEBUG: Session pid=1463: Exited with return value 0
[+8.25s] DEBUG: Seat: Session stopped
[+8.31s] DEBUG: Session pid=1816: Got 1 message(s) from PAM
[+8.54s] DEBUG: Process 1194 exited with return value 0
[+8.54s] DEBUG: DisplayServer x-0: X server stopped
[+8.54s] DEBUG: Releasing VT 7
[+8.54s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+8.54s] DEBUG: Seat: Display server stopped

```

I am experiencing on all my system Amd and nvidia based.

---

