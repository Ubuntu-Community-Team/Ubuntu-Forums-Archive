---
title: "Shutdown freeze"
date: 2018-11-15
forum: General Help
---

### Post by wpsd on 2018-11-15
Hi recently, my laptop cannot be shutdown it said reached target shutdown, but stay there freezing. I'm not sure what I change. Currently I have to forcefully shutdown using power button.

It happen both during plug / unplug electricity. Maybe 4 out of 5 always freeze. Not sure whats the problem

This is my spec  
My laptop is Lenovo Yoga370  

 - Gnome Ubuntu 16.04.5 
 - Kernel 4.15.0-39-generic #42~16.04.1-Ubuntu SMP Wed Oct 24 17:09:54 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

I'm not sure how to debug since during freeze I cannot do anything. I try enable debug-shell in systemd, but I cannot access tty9 when freeze so it's useless.

This is the only log I have during shutdown from syslog, kern.log also doesn't show anything

 ```
   Nov 15 18:45:02 firefox.desktop[4393]: [Parent 4393, Gecko_IOThread] WARNING: pipe error (47): Connection reset by peer: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 356
    Nov 15 18:45:02 firefox.desktop[4393]: [Parent 4393, Gecko_IOThread] WARNING: pipe error (95): Connection reset by peer: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 356
    Nov 15 18:45:02 firefox.desktop[4393]: [Parent 4393, Gecko_IOThread] WARNING: pipe error (143): Connection reset by peer: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 356
    Nov 15 18:45:02 firefox.desktop[4393]: [Parent 4393, Gecko_IOThread] WARNING: pipe error (175): Connection reset by peer: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 356
    Nov 15 18:45:11 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:45:11 gnome-session[2451]: This incident has been reported.
    Nov 15 18:45:12 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:45:12 gnome-session[2451]: This incident has been reported.
    Nov 15 18:45:31 bluetoothd[1105]: Terminating
    Nov 15 18:45:31 systemd[1]: Stopping Bluetooth service...
    Nov 15 18:45:31 systemd[1]: Stopped target Sound Card.
    Nov 15 18:45:31 systemd[1]: Stopping Manage, Install and Generate Color Profiles...
    Nov 15 18:45:31 systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
    Nov 15 18:45:31 systemd[1]: Stopping ACPI event daemon...
    Nov 15 18:45:31 /usr/lib/gdm3/gdm-x-session[2859]: Resource temporarily unavailable: Resource temporarily unavailable
    Nov 15 18:45:31 /usr/lib/gdm3/gdm-x-session[2859]: message repeated 12 times: [ Resource temporarily unavailable: Resource temporarily unavailable]
    Nov 15 18:45:31 /usr/lib/gdm3/gdm-x-session[2859]: Permission denied: Permission denied
    Nov 15 18:45:31 /usr/lib/gdm3/gdm-x-session[2859]: message repeated 35 times: [ Permission denied: Permission denied]
    Nov 15 18:45:31 bluetoothd[1105]: Stopping SDP server
    Nov 15 18:45:31 dockerd[1629]: time="2018-11-15T18:45:31.305453477+07:00" level=info msg="Processing signal 'terminated'"
    Nov 15 18:45:31 gnome-session[2874]: gnome-session-binary[2874]: WARNING: Lost name on bus: org.gnome.SessionManager
    Nov 15 18:45:31 gnome-session[2874]: gnome-session-binary[2874]: CRITICAL: We failed, but the fail whale is dead. Sorry....
    Nov 15 18:45:31 systemd[1]: Stopping Session 1 of user wiryono.
    Nov 15 18:45:31 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1131" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

I have powertop --auto-tune during startup, it's been running ok for 1 year now, then suddenly this happen. Try to disable it but the problem still presist

I also see a lot of red message in syslog, I'm not sure if this relevant

```

    Nov 15 18:41:08 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:41:08 gnome-session[2451]: This incident has been reported.
    Nov 15 18:41:16 firefox.desktop[4393]: [Parent 4393, Gecko_IOThread] WARNING: pipe error: Broken pipe: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 729
    Nov 15 18:41:16 firefox.desktop[4393]: message repeated 6 times: [ [Parent 4393, Gecko_IOThread] WARNING: pipe error: Broken pipe: file /build/firefox-j7tNrI/firefox-63.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 729]
    Nov 15 18:41:28 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:41:28 gnome-session[2451]: This incident has been reported.
    Nov 15 18:41:40 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:41:40 gnome-session[2451]: This incident has been reported.
    Nov 15 18:41:41 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:41:41 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:34 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:34 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:35 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:35 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:37 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:37 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:37 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:37 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:44 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:44 gnome-session[2451]: This incident has been reported.
    Nov 15 18:43:45 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:43:45 gnome-session[2451]: This incident has been reported.
    Nov 15 18:44:14 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:44:14 gnome-session[2451]: This incident has been reported.
    Nov 15 18:44:15 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:44:15 gnome-session[2451]: This incident has been reported.
    Nov 15 18:44:16 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:44:16 gnome-session[2451]: This incident has been reported.
    Nov 15 18:44:16 gnome-session[2451]: Error executing command as another user: Not authorized
    Nov 15 18:44:16 gnome-session[2451]: This incident has been reported.

```

Sometime my gnome freeze (keyboard dead) during login, Don't know why... I also have USB plug/unplug freeze problem also recently. The forum said try disabling any gnome extensions for this one.

So currently I remove all extensions from /usr/share/gnome-shell/extensions and .local/share/gnome-shell/extensions this way not a single extension is running, seems work for usb. But the shutdown still a problem.

I remember during 14.04 or something I also has this problem, I believe forcing shutdown will degrading my laptop battery overtime

---

