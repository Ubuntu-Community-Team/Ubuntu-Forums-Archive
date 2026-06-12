---
title: "How clean is your boot log?"
date: 2021-12-08
forum: General Help
---

### Post by yaminb on 2021-12-08
I need a reference as to how clean a bootlog should be?
My system is functioning well enough, but I see some entries in the bootlog. I'm just wondering how abnormal these are?


```
journalctl -p err -b
-- Journal begins at Wed 2021-07-21 08:55:40 EDT, ends at Wed 2021-12-08 09:47:09 EST. --
Dec 08 09:17:14 -desktop kernel: 
Dec 08 09:17:14 -desktop systemd-udevd[505]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
Dec 08 09:17:15 -desktop kernel: nvidia-gpu 0000:06:00.3: i2c timeout error e0000000
Dec 08 09:17:15 -desktop kernel: ucsi_ccg 1-0008: i2c_transfer failed -110
Dec 08 09:17:15 -desktop kernel: ucsi_ccg 1-0008: ucsi_ccg_init failed - -110
Dec 08 09:17:16 -desktop cachefilesd[1667]: /etc/cachefilesd.conf:19:CacheFiles gave config error: Invalid argument
Dec 08 09:17:16 -desktop systemd[1]: Failed to start LSB: CacheFiles daemon.
Dec 08 09:17:16 -desktop kernel: CacheFiles: Free space limits must be in range 0%<=stop<cull<run<100%
Dec 08 09:17:18 -desktop kernel: overlayfs: missing 'lowerdir'
Dec 08 09:17:28 -desktop gdm-password][2721]: gkr-pam: unable to locate daemon control file
Dec 08 09:17:29 -desktop systemd[2878]: Failed to start Application launched by gnome-session-binary.
Dec 08 09:17:29 -desktop systemd[2878]: Failed to start Application launched by gnome-session-binary.
Dec 08 09:17:29 -desktop systemd[2878]: Failed to start Application launched by gnome-session-binary.
Dec 08 09:17:33 -desktop gdm-launch-environment][1783]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Dec 08 09:17:43 -desktop pipewire-media-session[2888]: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut
Dec 08 09:17:47 -desktop systemd[1]: Failed to start Process error reports when automatic reporting is enabled.

```

---

