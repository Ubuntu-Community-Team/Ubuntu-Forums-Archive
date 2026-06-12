---
title: "Xubuntu 20.04 autologin failing."
date: 2020-12-11
forum: General Help
---

### Post by Phill_Harvey-Smith on 2020-12-11
Hi all,

We have an intel nuc that we use as an information desplay server in our departmental common room. The machine is running Xubuntu 20.04 (upgraded from 18.04). The machine is configured to autologin but on re-boot is just dropping to a login screen.

In /etc/lightdm/lightdm.conf we have : 
```
[Seat:*]
autologin-guest=false
autologin-user=statsusr
autologin-user-timeout=0
xserver-command=X -s 0 -dpms

```

looking at the log files in /var/log/lightdm :

lightdm.log contains :
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.30.0, UID=0 PID=486
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: _g_io_module_get_default: Found default implementation local (GLocalVfs) for ‘gio-vfs’
[+0.02s] DEBUG: Monitoring logind for seats
[+0.02s] DEBUG: New seat added from logind: seat0
[+0.02s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.02s] DEBUG: Seat seat0: Starting
[+0.02s] DEBUG: Seat seat0: Creating user session
[+0.02s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.15s] DEBUG: User /org/freedesktop/Accounts/User1001 added
[+0.16s] DEBUG: Seat seat0: Creating display server of type x
[+0.16s] DEBUG: posix_spawn avoided (fd close requested) 
[+0.17s] DEBUG: Using VT 7
[+0.17s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.17s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.17s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.17s] DEBUG: XServer 0: Launching X Server
[+0.17s] DEBUG: Launching process 534: /usr/bin/X -s 0 -dpms :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.17s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.17s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.17s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.17s] DEBUG: posix_spawn avoided (automatic reaping requested) (fd close requested) 
[+1.06s] DEBUG: Got signal 10 from process 534
[+1.06s] DEBUG: XServer 0: Got signal from X server :0
[+1.06s] DEBUG: XServer 0: Connecting to XServer :0
[+2.06s] DEBUG: posix_spawn avoided (fd close requested) (child_setup specified) 
[+2.06s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+2.06s] DEBUG: Session pid=694: Started with service 'lightdm-autologin', username 'statsusr'
[+2.11s] DEBUG: Session pid=694: Authentication complete with return value 0: Success
[+2.11s] DEBUG: Seat seat0: Session authenticated, running command
[+2.11s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+2.11s] DEBUG: posix_spawn avoided (fd close requested) (child_setup specified) 
[+2.11s] DEBUG: Session pid=694: Running command /usr/sbin/lightdm-session startxfce4
[+2.11s] DEBUG: Creating shared data directory /var/lib/lightdm-data/statsusr
[+2.11s] DEBUG: Session pid=694: Logging to .xsession-errors
[+2.42s] DEBUG: Activating VT 7
[+2.42s] DEBUG: Activating login1 session c1
[+2.42s] DEBUG: Seat seat0 changes active session to c1
[+2.42s] DEBUG: Session c1 is already active
[+3.28s] DEBUG: Session pid=694: Exited with return value 1
[+3.28s] DEBUG: Seat seat0: Session stopped
[+3.34s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+3.34s] DEBUG: Sending signal 15 to process 534
[+3.72s] DEBUG: Process 534 terminated with signal 6
[+3.72s] DEBUG: XServer 0: X server stopped
[+3.72s] DEBUG: Releasing VT 7
[+3.72s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+3.72s] DEBUG: Seat seat0: Display server stopped
[+3.72s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+3.72s] DEBUG: Seat seat0: Creating greeter session
[+3.72s] DEBUG: Seat seat0: Creating display server of type x
[+3.72s] DEBUG: Using VT 7
[+3.72s] DEBUG: Seat seat0: Starting local X display on VT 7
[+3.72s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+3.72s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+3.72s] DEBUG: XServer 0: Launching X Server
[+3.72s] DEBUG: Launching process 864: /usr/bin/X -s 0 -dpms :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+3.72s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+4.44s] DEBUG: Got signal 10 from process 864
[+4.44s] DEBUG: XServer 0: Got signal from X server :0
[+4.44s] DEBUG: XServer 0: Connecting to XServer :0
[+4.49s] DEBUG: posix_spawn avoided (fd close requested) (child_setup specified) 
[+4.49s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+4.49s] DEBUG: Session pid=879: Started with service 'lightdm-greeter', username 'lightdm'
[+4.51s] DEBUG: Session pid=879: Authentication complete with return value 0: Success
[+4.51s] DEBUG: Seat seat0: Session authenticated, running command
[+4.51s] DEBUG: Launching process 882: xubuntu-numlockx
[+4.65s] DEBUG: Process 882 exited with return value 0
[+4.65s] DEBUG: Seat seat0: Exit status of xubuntu-numlockx: 0
[+4.65s] DEBUG: Session pid=879: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+4.65s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+4.65s] DEBUG: Session pid=879: Logging to /var/log/lightdm/seat0-greeter.log
[+4.85s] DEBUG: Activating VT 7
[+4.85s] DEBUG: Activating login1 session c2
[+4.85s] DEBUG: Seat seat0 changes active session to c2
[+4.85s] DEBUG: Session c2 is already active
[+5.08s] DEBUG: Greeter connected version=1.30.0 api=1 resettable=false
[+5.53s] DEBUG: Greeter start authentication for itadmin
[+5.53s] DEBUG: Session pid=971: Started with service 'lightdm', username 'itadmin'
[+5.55s] DEBUG: Session pid=971: Got 1 message(s) from PAM
[+5.55s] DEBUG: Prompt greeter with 1 message(s)
```

If I'm reading that correctly it tries to start something which dies :(

x-0.log contains :

```

X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.15.0-124-generic x86_64 Ubuntu
Current Operating System: Linux crdisplay 5.4.0-56-generic #62~18.04.1-Ubuntu SMP Tue Nov 24 10:07:50 UTC 2020 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-56-generic root=UUID=7ba381e6-d61f-489f-ae9c-a7e462ea269c ro quiet
Build Date: 30 November 2020  05:56:33PM
xorg-server 2:1.20.8-2ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.38.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 11 09:55:16 2020
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Xorg: ../../../../dix/privates.c:384: dixRegisterPrivateKey: Assertion `!global_keys[type].created' failed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/lib/xorg/Xorg (OsLookupColor+0x13c) [0x560b02b1c52c]
(EE) 1: /lib/x86_64-linux-gnu/libpthread.so.0 (funlockfile+0x60) [0x7fa67ee8641f]
(EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (gsignal+0xcb) [0x7fa67ecc318b]
(EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (abort+0x12b) [0x7fa67eca2859]
(EE) unw_get_proc_name failed: no unwind info found [-10]
(EE) 4: /lib/x86_64-linux-gnu/libc.so.6 (?+0x0) [0x7fa67eca271a]
(EE) 5: /lib/x86_64-linux-gnu/libc.so.6 (__assert_fail+0x46) [0x7fa67ecb3f36]
(EE) 6: /usr/lib/xorg/Xorg (dixRegisterPrivateKey+0x239) [0x560b029d9a79]
(EE) 7: /usr/lib/xorg/modules/libglamoregl.so (glamor_init+0xcf) [0x7fa6741a935f]
(EE) unw_get_proc_name failed: no unwind info found [-10]
(EE) 8: /usr/lib/xorg/modules/drivers/modesetting_drv.so (?+0x0) [0x7fa67e6637b0]
(EE) unw_get_proc_name failed: no unwind info found [-10]
(EE) 9: /usr/lib/xorg/modules/drivers/modesetting_drv.so (?+0x0) [0x7fa67e65bb40]
(EE) 10: /usr/lib/xorg/Xorg (AddGPUScreen+0xf5) [0x560b029bb2d5]
(EE) 11: /usr/lib/xorg/Xorg (xf86PlatformMatchDriver+0xa44) [0x560b02a16ca4]
(EE) 12: /usr/lib/xorg/Xorg (xf86PlatformDeviceCheckBusID+0x225) [0x560b02a1bfe5]
(EE) 13: /usr/lib/xorg/Xorg (config_fini+0xa4a) [0x560b02a1888a]
(EE) 14: /usr/lib/xorg/Xorg (config_fini+0x1408) [0x560b02a19cf8]
(EE) 15: /usr/lib/xorg/Xorg (OsCleanup+0x5c1) [0x560b02b1d3b1]
(EE) 16: /usr/lib/xorg/Xorg (WaitForSomething+0x193) [0x560b02b15c13]
(EE) 17: /usr/lib/xorg/Xorg (SendErrorToClient+0x117) [0x560b029bacf7]
(EE) 18: /usr/lib/xorg/Xorg (InitFonts+0x3b4) [0x560b029befc4]
(EE) 19: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0x7fa67eca40b3]
(EE) 20: /usr/lib/xorg/Xorg (_start+0x2e) [0x560b029a8a2e]
(EE) 
(EE) 
Fatal server error:
(EE) Caught signal 6 (Aborted). Server aborting
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.

X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.15.0-124-generic x86_64 Ubuntu
Current Operating System: Linux crdisplay 5.4.0-56-generic #62~18.04.1-Ubuntu SMP Tue Nov 24 10:07:50 UTC 2020 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-56-generic root=UUID=7ba381e6-d61f-489f-ae9c-a7e462ea269c ro quiet
Build Date: 30 November 2020  05:56:33PM
xorg-server 2:1.20.8-2ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.38.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 11 09:55:20 2020
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
```

Which seems to suggest that the x server is dying :(

I'm using the integrated intel graphics drivers but have modified the /etc/default/grub and removed "splash" from GRUB_CMDLINE_LINUX_DEFAULT and then reran update-grub as this was suggested as being a source of problems.

I also have xrdp installed and can login to the statsusr account via that without problems and it works as expected.

Does anyone have any clues as to what might be causing the server to die, and autologin to not work?

Cheers.

Phill.

---

### Post by Phill_Harvey-Smith on 2020-12-15
I seem to have solved it using :

[https://bugs.freedesktop.org/show_bug.cgi?id=107226](https://bugs.freedesktop.org/show_bug.cgi?id=107226)

By adding i915 to my /etc/initramfs-tools/modules and re-generatin initramfs with update-initramfs -u and then re-booting.

Cheers.

Phill.

---

