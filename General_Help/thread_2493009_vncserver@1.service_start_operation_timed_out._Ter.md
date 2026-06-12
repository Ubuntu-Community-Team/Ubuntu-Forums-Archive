---
title: "vncserver@1.service: start operation timed out. Terminating."
date: 2023-11-30
forum: General Help
---

### Post by isprins on 2023-11-30
Hello,- I have followed this tutorial:
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

There's something going on that I dont understand:

```
sudo systemctl status vncserver@1
× vncserver@1.service - Start TightVNC server at startup
     Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
     Active: failed (Result: timeout) since Thu 2023-11-30 11:32:38 UTC; 2min 2s ago
    Process: 3547766 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=2)
    Process: 3547770 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :1 (code=exited, status=0/SUCCESS)
        CPU: 4.690s

Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.freedesktop.Notifications'
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Nov 30 11:31:07 haaken-media org.freedesktop.Notifications[3547907]: Another notification daemon is running, exiting
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.freedesktop.thumbnails.Thumbnailer1'
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Activating service name='org.gtk.vfs.Metadata' requested by ':1.11' (uid=1000 pid=3547860 comm="xfdesktop " label="unco>
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.gtk.vfs.Metadata'
Nov 30 11:32:35 haaken-media systemd[1]: vncserver@1.service: start operation timed out. Terminating.
Nov 30 11:32:38 haaken-media systemd[1]: vncserver@1.service: Failed with result 'timeout'.
Nov 30 11:32:38 haaken-media systemd[1]: Failed to start Start TightVNC server at startup.
Nov 30 11:32:38 haaken-media systemd[1]: vncserver@1.service: Consumed 4.690s CPU time.
...skipping...
× vncserver@1.service - Start TightVNC server at startup
     Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
     Active: failed (Result: timeout) since Thu 2023-11-30 11:32:38 UTC; 2min 2s ago
    Process: 3547766 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=2)
    Process: 3547770 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :1 (code=exited, status=0/SUCCESS)
        CPU: 4.690s

Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.freedesktop.Notifications'
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Nov 30 11:31:07 haaken-media org.freedesktop.Notifications[3547907]: Another notification daemon is running, exiting
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.freedesktop.thumbnails.Thumbnailer1'
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Activating service name='org.gtk.vfs.Metadata' requested by ':1.11' (uid=1000 pid=3547860 comm="xfdesktop " label="unco>
Nov 30 11:31:07 haaken-media dbus-daemon[3547802]: [session uid=1000 pid=3547800] Successfully activated service 'org.gtk.vfs.Metadata'
Nov 30 11:32:35 haaken-media systemd[1]: vncserver@1.service: start operation timed out. Terminating.
Nov 30 11:32:38 haaken-media systemd[1]: vncserver@1.service: Failed with result 'timeout'.
Nov 30 11:32:38 haaken-media systemd[1]: Failed to start Start TightVNC server at startup.
Nov 30 11:32:38 haaken-media systemd[1]: vncserver@1.service: Consumed 4.690s CPU time.


```

What is causing this ?

---

