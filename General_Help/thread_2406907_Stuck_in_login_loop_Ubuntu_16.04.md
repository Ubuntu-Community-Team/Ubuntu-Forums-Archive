---
title: "Stuck in login loop Ubuntu 16.04"
date: 2018-11-27
forum: General Help
---

### Post by jjeremydiaz-rex on 2018-11-27
I need some advice for working towards a resolution to my current login loop issue in Ubuntu Desktop 16.04. When I try to sign in locally, after I input the correct password, the gui prompts for the login credentials again.

Here are a few things I have tried:

1. Ran dpkg-reconfigure lightdm
2. Double check .xauthority and .ICEauthority permissions
3. Remove both .xauthority and .ICEauthority, reboot, and try to log in with the newly generated .xauthority and .ICEauthority
4. Restart lightdm
5. Check for any disk space issues

A few things I have not tried yet since I do not want to risk breaking the server unless i'm sure of the issue:

1. Reinstall lightdm
2. Reinstall GPU drivers (currently have amd GPU with radeon drivers)
3. Uninstall lightdm and install lxdm
4. Uninstall lightdm and install gdm

Here are some log file outputs:

syslog:

```


Nov 27 15:18:05 dummy org.gtk.vfs.Daemon[12182]: A connection to the bus can't be made
Nov 27 15:18:06 dummy systemd[1]: Started Session c2 of user gore.
Nov 27 15:18:06 dummy org.ayatana.bamf[15489]: bamfdaemon start/running, process 15537
Nov 27 15:18:08 dummy org.a11y.atspi.Registry[15643]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 27 15:18:08 dummy gnome-session[15628]: gnome-session-is-accelerated: No hardware 3D support.
Nov 27 15:18:08 dummy gnome-session[15628]: gnome-session-check-accelerated: Helper exited with code 256
Nov 27 15:18:08 dummy gnome-session[15628]: gnome-session-binary[15628]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 27 15:18:08 dummy gnome-session-binary[15628]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 27 15:18:08 dummy lightdm[1287]: ** (lightdm:1287): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Nov 27 15:18:09 dummy systemd[1]: Started Session c3 of user lightdm.
Nov 27 15:18:09 dummy org.a11y.atspi.Registry[15720]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 27 15:18:09 dummy dbus[1033]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'



```

.xsession-errors:

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (15628) terminated with status 1
upstart: unity-settings-daemon main process (15620) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (15479) killed by TERM signal
upstart: update-notifier-crash (/var/crash/_sbin_upstart.109.crash) main process (15523) killed by TERM signal
upstart: bamfdaemon main process (15537) killed by TERM signal
upstart: upstart-dbus-session-bridge main process (15552) terminated with status 1
upstart: hud main process (15618) killed by TERM signal
upstart: unity7 pre-start process (15622) terminated with status 143
upstart: unity-panel-service main process (15640) killed by TERM signal

```

.xsession-errors-old:

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (12097) terminated with status 1
upstart: unity-settings-daemon main process (12090) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (11939) killed by TERM signal
upstart: update-notifier-crash (/var/crash/_sbin_upstart.109.crash) main process (11989) killed by TERM signal
upstart: hud main process (12088) killed by TERM signal
upstart: bamfdaemon main process (11999) killed by TERM signal
upstart: unity7 pre-start process (12092) terminated with status 143
upstart: unity-panel-service main process (12114) killed by TERM signal

```

seat0-greeter.log:

```

[+0.07s] DEBUG: user-list.vala:1012: Adding guest account entry
[+0.22s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.22s] DEBUG: Starting authentication for user gore...
[+0.22s] DEBUG: Wrote 20 bytes to daemon
[+0.22s] DEBUG: main-window.vala:185: Screen is 1024x768 pixels
[+0.22s] DEBUG: main-window.vala:193: Monitor 0 is 1024x768 pixels at 0,0
[+0.22s] DEBUG: unity-greeter.vala:573: Showing greeter
[+0.22s] DEBUG: unity-greeter.vala:257: Showing main window
[+0.23s] DEBUG: background.vala:483: Regenerating backgrounds
[+0.23s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1024x768
[+0.23s] DEBUG: unity-greeter.vala:616: Starting main loop
[+0.23s] DEBUG: Read 8 bytes from daemon
[+0.23s] DEBUG: Read 34 bytes from daemon
[+0.23s] DEBUG: Prompt user with 1 message(s)
[+0.25s] DEBUG: user-list.vala:1030: Adding/updating user gore (GORE2)
[+0.26s] DEBUG: settings-daemon.vala:75: Acquired org.gnome.SessionManager
[+0.26s] DEBUG: settings-daemon.vala:102: Acquired org.gnome.ScreenSaver
[+0.26s] DEBUG: settings-daemon.vala:159: All bus names acquired, starting unity-settings-daemon
[+0.27s] DEBUG: Connected to Application Indicator Service.
[+0.27s] DEBUG: User /org/freedesktop/Accounts/User109 added
[+0.29s] DEBUG: menubar.vala:537: Adding indicator object 0x18e13d0 at position 0
[+0.30s] DEBUG: menubar.vala:537: Adding indicator object 0x18e17f0 at position 1
[+0.30s] DEBUG: menubar.vala:537: Adding indicator object 0x18e1530 at position 1
[+0.30s] DEBUG: Request current apps
[+0.32s] DEBUG: unity-greeter.vala:240: starting system-ready sound
[+0.33s] DEBUG: menubar.vala:537: Adding indicator object 0x18e1270 at position 3


** (unity-settings-daemon:15805): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'
[+0.37s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete


(unity-settings-daemon:15805): color-plugin-WARNING **: failed to get edid: unable to get EDID for output


(nm-applet:15757): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkWidget'


(nm-applet:15757): Gtk-CRITICAL **: gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed
[+0.39s] DEBUG: Building new application entry: :1.15  with icon: nm-device-wired at position 0
[+0.39s] DEBUG: menubar.vala:537: Adding indicator object 0x1927800 at position 4


(unity-settings-daemon:15805): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output
[+299.90s] DEBUG: settings-daemon.vala:209: Screensaver activated


(unity-settings-daemon:15805): power-plugin-WARNING **: failed to turn the kbd backlight off: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.freedesktop.UPower.KbdBacklight' on object at path /org/freedesktop/UPower/KbdBacklight

```

lightdm.log:

```

[+8258.21s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+8258.21s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+8258.21s] DEBUG: DisplayServer x-0: Launching X Server
[+8258.21s] DEBUG: Launching process 12165: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7
-novtswitch
[+8258.21s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+8258.34s] DEBUG: Got signal 10 from process 12165
[+8258.34s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+8258.34s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+8258.34s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+8258.34s] DEBUG: Session pid=12170: Started with service 'lightdm-greeter', username 'lightdm'
[+8258.35s] DEBUG: Session pid=12170: Authentication complete with return value 0: Success
[+8258.35s] DEBUG: Seat seat0: Session authenticated, running command
[+8258.35s] DEBUG: Session pid=12170: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+8258.35s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+8258.35s] DEBUG: Session pid=12170: Logging to /var/log/lightdm/seat0-greeter.log
[+8258.38s] DEBUG: Activating VT 7
[+8258.38s] DEBUG: Activating login1 session c3
[+8258.38s] DEBUG: Seat seat0 changes active session to c3
[+8258.38s] DEBUG: Session c3 is already active
[+8258.48s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+8258.58s] DEBUG: Greeter start authentication for gore
[+8258.58s] DEBUG: Session pid=12217: Started with service 'lightdm', username 'gore'
[+8258.59s] DEBUG: Session pid=12217: Got 1 message(s) from PAM
[+8258.59s] DEBUG: Prompt greeter with 1 message(s)
[+8258.64s] DEBUG: User /org/freedesktop/Accounts/User109 added
[+10438.54s] DEBUG: Seat seat0 changes active session to c3
[+10438.54s] DEBUG: Session c3 is already active
[+12092.44s] DEBUG: Continue authentication
[+12092.46s] DEBUG: Session pid=12217: Authentication complete with return value 0: Success
[+12092.46s] DEBUG: Authenticate result for user gore: Success
[+12092.46s] DEBUG: User gore authorized
[+12092.47s] DEBUG: Greeter requests session ubuntu
[+12092.47s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+12092.47s] DEBUG: Session pid=12170: Sending SIGTERM
[+12092.48s] DEBUG: Session pid=12170: Exited with return value 0
[+12092.48s] DEBUG: Seat seat0: Session stopped
[+12092.48s] DEBUG: Seat seat0: Greeter stopped, running session
[+12092.48s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session7
[+12092.48s] DEBUG: Session pid=12217: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+12092.48s] DEBUG: Creating shared data directory /var/lib/lightdm-data/gore
[+12092.48s] DEBUG: Session pid=12217: Logging to .xsession-errors
[+12092.52s] DEBUG: Activating VT 7
[+12092.52s] DEBUG: Activating login1 session c2
[+12092.52s] DEBUG: Seat seat0 changes active session to c2
[+12092.52s] DEBUG: Session c2 is already active
[+12095.27s] DEBUG: Session pid=12217: Exited with return value 0
[+12095.27s] DEBUG: Seat seat0: Session stopped
[+12095.27s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+12095.27s] DEBUG: Sending signal 15 to process 12165
[+12095.27s] DEBUG: Seat seat0 changes active session to
[+12095.27s] CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed
[+12095.39s] DEBUG: Process 12165 exited with return value 0
[+12095.39s] DEBUG: DisplayServer x-0: X server stopped
[+12095.39s] DEBUG: Releasing VT 7
[+12095.39s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+12095.39s] DEBUG: Seat seat0: Display server stopped
[+12095.39s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+12095.39s] DEBUG: Seat seat0: Creating greeter session
[+12095.39s] DEBUG: Seat seat0: Creating display server of type x
[+12095.39s] DEBUG: Using VT 7
[+12095.39s] DEBUG: Seat seat0: Starting local X display on VT 7
[+12095.39s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+12095.39s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+12095.39s] DEBUG: DisplayServer x-0: Launching X Server
[+12095.39s] DEBUG: Launching process 15695: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+12095.39s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+12095.53s] DEBUG: Got signal 10 from process 15695
[+12095.53s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+12095.53s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+12095.53s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+12095.53s] DEBUG: Session pid=15700: Started with service 'lightdm-greeter', username 'lightdm'
[+12095.54s] DEBUG: Session pid=15700: Authentication complete with return value 0: Success
[+12095.54s] DEBUG: Seat seat0: Session authenticated, running command
[+12095.54s] DEBUG: Session pid=15700: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+12095.55s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+12095.55s] DEBUG: Session pid=15700: Logging to /var/log/lightdm/seat0-greeter.log
[+12095.57s] DEBUG: Activating VT 7
[+12095.57s] DEBUG: Activating login1 session c3
[+12095.57s] DEBUG: Seat seat0 changes active session to c3
[+12095.57s] DEBUG: Session c3 is already active
[+12095.67s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+12095.86s] DEBUG: Greeter start authentication for gore
[+12095.86s] DEBUG: Session pid=15751: Started with service 'lightdm', username 'gore'
[+12095.86s] DEBUG: Session pid=15751: Got 1 message(s) from PAM
[+12095.86s] DEBUG: Prompt greeter with 1 message(s)
[+12095.91s] DEBUG: User /org/freedesktop/Accounts/User109 added
[+13895.66s] DEBUG: Seat seat0 changes active session to c3
[+13895.66s] DEBUG: Session c3 is already active


```

x-0.log:

```

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-128-generic x86_64 Ubuntu
Current Operating System: Linux gore2 4.4.0-139-generic #165-Ubuntu SMP Wed Oct 24 10:58:50 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-139-generic.efi.signed root=UUID=5f2c1474-2b5b-4a29-aca2-f14da78dd179 ro quiet splash vt.handoff=7
Build Date: 10 August 2018  09:33:05AM
xorg-server 2:1.18.4-0ubuntu0.8 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 27 14:14:11 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) Server terminated successfully (0). Closing log file.


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-128-generic x86_64 Ubuntu
Current Operating System: Linux gore2 4.4.0-139-generic #165-Ubuntu SMP Wed Oct 24 10:58:50 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-139-generic.efi.signed root=UUID=5f2c1474-2b5b-4a29-aca2-f14da78dd179 ro quiet splash vt.handoff=7
Build Date: 10 August 2018  09:33:05AM
xorg-server 2:1.18.4-0ubuntu0.8 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 27 15:18:08 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"



```

Xorg.0.log:

```

[ 12116.465] (II) No input driver specified, ignoring this device.
[ 12116.465] (II) This device may have been added with another device file.
[ 12116.465] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event13)
[ 12116.465] (II) No input driver specified, ignoring this device.
[ 12116.465] (II) This device may have been added with another device file.
[ 12116.466] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event14)
[ 12116.466] (II) No input driver specified, ignoring this device.
[ 12116.466] (II) This device may have been added with another device file.
[ 12116.466] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event15)
[ 12116.466] (II) No input driver specified, ignoring this device.
[ 12116.466] (II) This device may have been added with another device file.
[ 12116.466] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event16)
[ 12116.466] (II) No input driver specified, ignoring this device.
[ 12116.466] (II) This device may have been added with another device file.
[ 12116.467] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event10)
[ 12116.467] (II) No input driver specified, ignoring this device.
[ 12116.467] (II) This device may have been added with another device file.
[ 12116.467] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event11)
[ 12116.467] (II) No input driver specified, ignoring this device.
[ 12116.467] (II) This device may have been added with another device file.
[ 12116.467] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event12)
[ 12116.467] (II) No input driver specified, ignoring this device.
[ 12116.467] (II) This device may have been added with another device file.
[ 12116.468] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[ 12116.468] (II) No input driver specified, ignoring this device.
[ 12116.468] (II) This device may have been added with another device file.
[ 12116.468] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event9)
[ 12116.468] (II) No input driver specified, ignoring this device.
[ 12116.468] (II) This device may have been added with another device file.
[ 12116.469] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 12116.469] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 12116.469] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 12116.469] (**) AT Translated Set 2 keyboard: always reports core events
[ 12116.469] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 12116.469] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 12116.469] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 12116.469] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 12116.469] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 12116.469] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[ 12116.469] (**) Option "xkb_rules" "evdev"
[ 12116.469] (**) Option "xkb_model" "pc105"
[ 12116.469] (**) Option "xkb_layout" "us"
[ 12116.471] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[ 12116.471] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 12116.471] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 12116.471] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 12116.471] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 12116.471] (**) Dell WMI hotkeys: always reports core events
[ 12116.471] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[ 12116.471] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[ 12116.471] (--) evdev: Dell WMI hotkeys: Found keys
[ 12116.471] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[ 12116.471] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[ 12116.471] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[ 12116.471] (**) Option "xkb_rules" "evdev"
[ 12116.471] (**) Option "xkb_model" "pc105"
[ 12116.471] (**) Option "xkb_layout" "us"


```


Thanks for any help!

---

