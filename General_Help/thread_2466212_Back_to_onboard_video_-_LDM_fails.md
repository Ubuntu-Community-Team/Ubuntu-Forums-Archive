---
title: "Back to onboard video - LDM fails"
date: 2021-08-23
forum: General Help
---

### Post by michalbo on 2021-08-23
First, please take it easy on me, I'm not very Linux savy...
For years my server was running on onboard video. Some time ago I added Nvidia card and all is good with it. Recently I decided to remove the add on card but I have a problem with the GUI start up while on mboard DVI (DVI to HDMI to be exact).
I did change the vido setting on my board pointing to onboard video. While booting I can see bios and then Ubuntu starting lines till the LDM. It stops after few trials and hangs there. The OS itself starts and runs ok.
Using SSH I can get those:
lines 1-13/13 (END)
```
&#9679; lightdm.service - Light Display Manager
     Loaded: loaded (/lib/systemd/system/lightdm.service; indirect; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2021-08-23 13:41:49 AWST; 52s ago
       Docs: man:lightdm(1)
    Process: 7247 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
    Process: 7250 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)
   Main PID: 7250 (code=exited, status=1/FAILURE)


Aug 23 13:41:49 ns1.mbo.id.au systemd[1]: lightdm.service: Scheduled restart job, restart counter is at 5.
Aug 23 13:41:49 ns1.mbo.id.au systemd[1]: Stopped Light Display Manager.
Aug 23 13:41:49 ns1.mbo.id.au systemd[1]: lightdm.service: Start request repeated too quickly.
Aug 23 13:41:49 ns1.mbo.id.au systemd[1]: lightdm.service: Failed with result 'exit-code'.
Aug 23 13:41:49 ns1.mbo.id.au systemd[1]: Failed to start Light Display Manager.
```

and this:

```
~$ sudo lightdm &#8211;-test-mode --debug
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.30.0, UID=0 PID=7692
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu-mate.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: _g_io_module_get_default: Found default implementation local (GLocalVfs) for ?gio-vfs?
[+0.00s] DEBUG: Monitoring logind for seats
[+0.00s] DEBUG: New seat added from logind: seat0
[+0.00s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.00s] DEBUG: Seat seat0: Starting
[+0.00s] DEBUG: Seat seat0: Creating greeter session
[+0.00s] DEBUG: Seat seat0: Creating display server of type x
[+0.00s] DEBUG: posix_spawn avoided (fd close requested)
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.00s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.00s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.00s] DEBUG: XServer 0: Launching X Server
[+0.00s] DEBUG: Launching process 7697: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.00s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.00s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1008 added
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User995 added
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User997 added
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User1007 added
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User1006 added
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User999 added
[+0.03s] DEBUG: User /org/freedesktop/Accounts/User998 added
[+0.45s] DEBUG: Process 7697 terminated with signal 6
[+0.45s] DEBUG: XServer 0: X server stopped
[+0.45s] DEBUG: Releasing VT 7
[+0.45s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.45s] DEBUG: Seat seat0: Display server stopped
[+0.45s] DEBUG: Launching process 7705: /sbin/prime-switch
[+0.55s] DEBUG: Process 7705 exited with return value 0
[+0.55s] DEBUG: Seat seat0: Exit status of /sbin/prime-switch: 0
[+0.55s] DEBUG: Seat seat0: Stopping session
[+0.55s] DEBUG: Seat seat0: Session stopped
[+0.55s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.55s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.55s] DEBUG: Seat seat0: Stopping
[+0.55s] DEBUG: Seat seat0: Stopped
[+0.55s] DEBUG: Required seat has stopped
[+0.55s] DEBUG: Stopping display manager
[+0.55s] DEBUG: Display manager stopped
[+0.55s] DEBUG: Stopping daemon
[+0.55s] DEBUG: Exiting with return value 1
```

Any pointers to what to start with will be appreciated.
Thanks

---

