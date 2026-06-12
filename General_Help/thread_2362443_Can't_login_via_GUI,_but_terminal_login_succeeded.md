---
title: "Can't login via GUI, but terminal login succeeded"
date: 2017-05-28
forum: General Help
---

### Post by orennn on 2017-05-28
Hey,

The general problem is that i can't login via GUI, but terminal login succeeded.
I'm using Ubuntu 14.04.

Have tried multiple solution:


sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
also have permission to .ICEauthority file.


[U][B]During login failure i receive the messages as follow:

[/B][/U]
file /var/log/lightdm/lightdm.log:
```
[+1274.19s] DEBUG: Session pid=7328: Continue authentication
[+1274.23s] DEBUG: Session pid=7377: Authentication complete with return value 0: Success
[+1274.23s] DEBUG: Session pid=7328: Authenticate result for user builder: Success
[+1274.23s] DEBUG: Session pid=7328: User builder authorized
[+1274.23s] DEBUG: Session pid=7328: Greeter requests session ubuntu
[+1274.23s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+1274.23s] DEBUG: Session pid=7328: Sending SIGTERM
[+1274.25s] DEBUG: Session pid=7328: Exited with return value 0
[+1274.25s] DEBUG: Seat: Session stopped
[+1274.25s] DEBUG: Seat: Greeter stopped, running session
[+1274.25s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session2
[+1274.25s] DEBUG: Session pid=7377: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+1274.25s] DEBUG: Creating shared data directory /var/lib/lightdm-data/builder
[+1274.25s] DEBUG: Session pid=7377: Logging to .xsession-errors
[+1274.28s] DEBUG: Activating VT 7
[+1274.28s] DEBUG: Activating login1 session c6
[+1275.43s] DEBUG: Session pid=7377: Exited with return value 0
[+1275.43s] DEBUG: Seat: Session stopped
[+1275.43s] DEBUG: Seat: Stopping display server, no sessions require it
[+1275.43s] DEBUG: Sending signal 15 to process 7321
[+1275.75s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+1276.10s] DEBUG: Process 7321 exited with return value 0
[+1276.10s] DEBUG: DisplayServer x-0: X server stopped
[+1276.10s] DEBUG: Releasing VT 7
[+1276.10s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1276.10s] DEBUG: Seat: Display server stopped
[+1276.10s] DEBUG: Launching process 7876: /sbin/prime-switch
[+1276.16s] DEBUG: Process 7876 exited with return value 0
[+1276.16s] DEBUG: Seat: Exit status of /sbin/prime-switch: 0
[+1276.16s] DEBUG: Seat: Active display server stopped, starting greeter
[+1276.16s] DEBUG: Seat: Creating greeter session
[+1276.16s] DEBUG: Seat: Creating display server of type x
[+1276.16s] DEBUG: Using VT 7
[+1276.16s] DEBUG: Seat: Starting local X display on VT 7
[+1276.16s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+1276.16s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+1276.16s] DEBUG: DisplayServer x-0: Launching X Server
[+1276.16s] DEBUG: Launching process 7896: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1276.16s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+1276.31s] DEBUG: Got signal 10 from process 7896
[+1276.31s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1276.31s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1276.31s] DEBUG: Launching process 7897: /sbin/prime-offload
[+1276.32s] DEBUG: Process 7897 exited with return value 0
[+1276.32s] DEBUG: Seat: Exit status of /sbin/prime-offload: 0
[+1276.32s] DEBUG: Seat: Display server ready, starting session authentication
[+1276.32s] DEBUG: Session pid=7903: Started with service 'lightdm-greeter', username 'lightdm'
[+1276.34s] DEBUG: Session pid=7903: Authentication complete with return value 0: Success
[+1276.34s] DEBUG: Seat: Session authenticated, running command
[+1276.34s] DEBUG: Session pid=7903: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+1276.34s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+1276.34s] DEBUG: Session pid=7903: Logging to /var/log/lightdm/x-0-greeter.log
[+1276.36s] DEBUG: Activating VT 7
[+1276.36s] DEBUG: Activating login1 session c7
[+1276.52s] DEBUG: Session pid=7903: Greeter connected version=1.10.6
[+1276.63s] DEBUG: Session pid=7903: Greeter start authentication for builder
[+1276.63s] DEBUG: Session pid=7952: Started with service 'lightdm', username 'builder'
[+1276.64s] DEBUG: Session pid=7952: Got 1 message(s) from PAM
[+1276.64s] DEBUG: Session pid=7903: Prompt greeter with 1 message(s)
[+1276.78s] DEBUG: User /org/freedesktop/Accounts/User1000 changed

```

file /var/log/lightdm/x-0-greeter.log:
```
[+300.17s] DEBUG: settings-daemon.vala:209: Screensaver activated
[+701.18s] DEBUG: settings-daemon.vala:211: Screensaver disabled
[+705.53s] DEBUG: Providing response to display manager
[+705.53s] DEBUG: Wrote 29 bytes to daemon
[+705.57s] DEBUG: Read 8 bytes from daemon
[+705.57s] DEBUG: Read 19 bytes from daemon
[+705.57s] DEBUG: Authentication complete for user builder with return code 0
[+705.57s] DEBUG: Starting session ubuntu
[+705.57s] DEBUG: Wrote 18 bytes to daemon
[+705.57s] DEBUG: Read 8 bytes from daemon
[+705.57s] DEBUG: Read 4 bytes from daemon
init: indicator-messages main process ended, respawning
init: indicator-bluetooth main process (7963) killed by TERM signal
init: indicator-bluetooth main process ended, respawning
[+705.59s] DEBUG: unity-greeter.vala:605: Got a SIGTERM
[+705.59s] DEBUG: settings-daemon.vala:78: Failed to acquire name org.gnome.SessionManager
[+705.59s] DEBUG: settings-daemon.vala:105: Failed to acquire name org.gnome.ScreenSaver
[+705.59s] DEBUG: unity-greeter.vala:135: Failed to acquire name com.canonical.Unity
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
[+705.59s] DEBUG: unity-greeter.vala:613: Cleaning up
[+705.59s] DEBUG: unity-greeter.vala:621: Upstart exited with return value 0
[+705.59s] DEBUG: unity-greeter.vala:633: AT-SPI exited with return value 0
[+705.59s] DEBUG: unity-greeter.vala:639: Exiting


** (unity-settings-daemon:7977): WARNING **: Name taken or bus went away - shutting down
init: indicator-power main process (7967) killed by TERM signal
init: indicator-datetime main process (7972) killed by TERM signal
init: indicator-session main process (7985) killed by TERM signal
init: indicator-application main process (7993) killed by TERM signal
init: indicator-bluetooth main process (8249) killed by TERM signal
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
nm-applet-Message: PID 7958 (we are 7958) sent signal 15, shutting down...


(nm-applet:7958): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed


(unity-settings-daemon:7977): dconf-WARNING **: failed to commit changes to dconf: The connection is closed
peer (g-io-error-quark, 0). Exiting.

```

file /var/log/auth.log
```
May 28 22:52:02 <hostname> lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
May 28 22:52:02 <hostname> lightdm: pam_unix(lightdm:session): session opened for user <user> by (uid=0)
May 28 22:52:03 <hostname> gnome-keyring-daemon[9243]: couldn't set environment variable<user> in session: The name org.gnome.SessionManager was not provided by any .service files
May 28 22:52:03 <hostname> lightdm: pam_unix(lightdm:session): session closed for user <user>
May 28 22:52:04 <hostname> lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
May 28 22:52:04 <hostname> lightdm: PAM adding faulty module: pam_kwallet.so
May 28 22:52:04 <hostname> lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
May 28 22:52:04 <hostname> lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
May 28 22:52:04 <hostname> lightdm: PAM adding faulty module: pam_kwallet.so
May 28 22:52:04 <hostname> lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "<user>"



```

Also tried to run "/usr/sbin/lightdm-session gnome-session --session=ubuntu" and received:
```
Running X session wrapper
Loading /etc/profile
Loading /home/builder/.profile
Loading resource: /etc/X11/Xresources/x11-common
xrdb: Can't open display ''
Loading X session script /etc/X11/Xsession.d/00upstart
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
: unsupported number of arguments (2); falling back to default session.
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/35x11-common_xhost-local
xhost:  unable to open display ""
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
xhost:  unable to open display ""
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/70im-config_launch
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/81overlay-scrollbar
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99upstart
Loading X session script /etc/X11/Xsession.d/99x11-common_start
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.


** (x-session-manager:8090): WARNING **: Cannot open display:

```

And also, when i have read i should try to edit in grub the line 
GRUB_CMDLINE_LINUX_DEFAULT and append init=/lib/systemd/systemd.
but systemd file doesnt exit on my ubuntu so the OS cannot startup.



As a last way, if it can be related, I also read that it might be something with my display.
so the result of the command because i don't know what how t o continue from here: "sudo lshw -C display"

```
[FONT=Verdana]  *-display
       description: VGA compatible controller
       product: SVGA II Adapter
       vendor: VMware
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=vmwgfx latency=64
       resources: irq:16 ioport:1070(size=16) memory:ec000000-efffffff memory:fe000000-fe7fffff memory:c0300000-c0307fff
[/FONT]

```

Please assist,
Thanks,
Oren.

---

### Post by rburkartjo on 2017-05-28
ore-bunch of stuff here
[https://journalxtra.com/linux/desktop-recovery/the-definitive-guide-to-getting-your-linux-desktop-back/](https://journalxtra.com/linux/desktop-recovery/the-definitive-guide-to-getting-your-linux-desktop-back/)

---

