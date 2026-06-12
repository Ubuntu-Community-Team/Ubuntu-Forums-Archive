---
title: "System Fault at Desktop"
date: 2019-12-02
forum: General Help
---

### Post by Quarkrad on 2019-12-02
Running 18.04.  I keep getting notice of a system fault at boot/Desktop and the option to report it.  I've cleared my syslog and re-booted.  There is a lot to view and most of it looks OK but the last few lines speak about **failed** and **Permission denied**.

```
Dec  2 10:57:13 dadubuntu systemd-timesyncd[809]: Synchronized to time server [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Dec  2 10:57:21 dadubuntu gvfsd-metadata[1630]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Dec  2 10:57:24 dadubuntu gvfsd-metadata[1630]: message repeated 15 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Dec  2 10:57:29 dadubuntu dbus-daemon[1187]: [session uid=1000 pid=1187] Activating service name='org.gnome.gedit' requested by ':1.28' (uid=1000 pid=1319 comm="caja " label="unconfined")
Dec  2 10:57:29 dadubuntu dbus-daemon[1187]: [session uid=1000 pid=1187] Successfully activated service 'org.gnome.gedit'
Dec  2 10:57:30 dadubuntu gedit[1889]: can't init metadata tree /home/dad/.local/share/gvfs-metadata/root: open: Permission denied
```

Does the above necessitate any action from me or do I need to look further 'up' the syslog file?

---

### Post by Quarkrad on 2019-12-02
Nothing to do with above.  Deleted my var/crash and var/log folders (to see what 'new' problems were being reported) and since then re-booted a number of times with no issues being reported.

---

