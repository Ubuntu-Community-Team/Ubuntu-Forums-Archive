---
title: "Journalctl -b help"
date: 2024-11-05
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-05
What is the root cause of these issue's and how to I fix them?


On this machine...
```
Acer Aspire E1-532
Lubuntu 22.04.5
```


Adverse things begin to happen then a few seconds later wifi disconnects.


The first symptom I notice is the mouse will start lagging.
I know that chances are the adversities start before the mouse lags.


Below is the journalctl -b 100 lines leading up to "kernel: ath: phy0:" adversities.


```
Nov 05 11:17:19 wyatt-aspiree1532 rtkit-daemon[937]: Supervising 5 threads of 3 processes of 1 users.
Nov 05 11:17:19 wyatt-aspiree1532 rtkit-daemon[937]: Successfully made thread 977 of process 900 owned by '1000' RT at priority 5.
Nov 05 11:17:19 wyatt-aspiree1532 rtkit-daemon[937]: Supervising 6 threads of 3 processes of 1 users.
Nov 05 11:17:21 wyatt-aspiree1532 systemd[879]: Started Sound Service.
Nov 05 11:17:21 wyatt-aspiree1532 systemd[879]: Reached target Main User Target.
Nov 05 11:17:21 wyatt-aspiree1532 systemd[879]: Startup finished in 5.867s.
Nov 05 11:17:21 wyatt-aspiree1532 pulseaudio[900]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
Nov 05 11:17:22 wyatt-aspiree1532 kernel: Bluetooth: RFCOMM TTY layer initialized
Nov 05 11:17:22 wyatt-aspiree1532 kernel: Bluetooth: RFCOMM socket layer initialized
Nov 05 11:17:22 wyatt-aspiree1532 kernel: Bluetooth: RFCOMM ver 1.11
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink/sbc
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource/sbc
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Nov 05 11:17:22 wyatt-aspiree1532 bluetoothd[588]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Nov 05 11:17:24 wyatt-aspiree1532 systemd[1]: systemd-fsckd.service: Deactivated successfully.
Nov 05 11:17:25 wyatt-aspiree1532 polkitd(authority=local)[600]: Registered Authentication Agent for unix-session:1 (system bus name :1.40 [/usr/bin/lxqt-policykit-agent], object path /org/lxqt/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov 05 11:17:25 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.17' (uid=1000 pid=1002 comm="/usr/bin/openbox " label="unconfined")
Nov 05 11:17:25 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service...
Nov 05 11:17:26 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.Daemon'
Nov 05 11:17:26 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service.
Nov 05 11:17:26 wyatt-aspiree1532 spice-vdagent[1049]: vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0 does not exist, exiting
Nov 05 11:17:27 wyatt-aspiree1532 kernel: warning: `kdeconnectd' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211
Nov 05 11:17:27 wyatt-aspiree1532 systemd-timesyncd[535]: Initial synchronization to time server 185.125.190.56:123 (ntp.ubuntu.com).
Nov 05 11:17:27 wyatt-aspiree1532 systemd-resolved[534]: Clock change detected. Flushing caches.
Nov 05 11:17:27 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.18' (uid=1000 pid=1011 comm="/usr/bin/pcmanfm-qt --desktop --profile=lxqt " label="unconfined")
Nov 05 11:17:27 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service - disk device monitor...
Nov 05 11:17:27 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Nov 05 11:17:27 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service - disk device monitor.
Nov 05 11:17:27 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.18' (uid=1000 pid=1011 comm="/usr/bin/pcmanfm-qt --desktop --profile=lxqt " label="unconfined")
Nov 05 11:17:27 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service - digital camera monitor...
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service - digital camera monitor.
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.18' (uid=1000 pid=1011 comm="/usr/bin/pcmanfm-qt --desktop --profile=lxqt " label="unconfined")
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service - Apple File Conduit monitor...
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service - Apple File Conduit monitor.
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.18' (uid=1000 pid=1011 comm="/usr/bin/pcmanfm-qt --desktop --profile=lxqt " label="unconfined")
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service - Media Transfer Protocol monitor...
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service - Media Transfer Protocol monitor.
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.18' (uid=1000 pid=1011 comm="/usr/bin/pcmanfm-qt --desktop --profile=lxqt " label="unconfined")
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Starting Virtual filesystem service - GNOME Online Accounts monitor...
Nov 05 11:17:28 wyatt-aspiree1532 dbus-daemon[955]: [session uid=1000 pid=955] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
Nov 05 11:17:28 wyatt-aspiree1532 systemd[879]: Started Virtual filesystem service - GNOME Online Accounts monitor.
Nov 05 11:17:33 wyatt-aspiree1532 dbus-daemon[590]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service' requested by ':1.46' (uid=1000 pid=1014 comm="/usr/bin/lxqt-panel " label="unconfined")
Nov 05 11:17:33 wyatt-aspiree1532 systemd[1]: Starting Daemon for power management...
Nov 05 11:17:33 wyatt-aspiree1532 dbus-daemon[590]: [system] Successfully activated service 'org.freedesktop.UPower'
Nov 05 11:17:33 wyatt-aspiree1532 systemd[1]: Started Daemon for power management.
Nov 05 11:17:34 wyatt-aspiree1532 systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Nov 05 11:17:39 wyatt-aspiree1532 systemd[1]: systemd-timedated.service: Deactivated successfully.
Nov 05 11:17:55 wyatt-aspiree1532 kernel: logitech-hidpp-device 0003:046D:4008.0003: HID++ 2.0 device connected.
Nov 05 11:17:56 wyatt-aspiree1532 upowerd[1129]: treated changed event as add on /sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.1/0003:046D:C52F.0002/0003:046D:4008.0003/power_supply/hidpp_battery_0
Nov 05 11:17:57 wyatt-aspiree1532 wpa_supplicant[608]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-35 noise=-89 txrate=72200
Nov 05 11:18:22 wyatt-aspiree1532 wpa_supplicant[608]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-34 noise=-88 txrate=72200
Nov 05 11:18:38 wyatt-aspiree1532 systemd[1]: Configuration file /run/systemd/system/netplan-ovs-cleanup.service is marked world-inaccessible. This has no effect as configuration data is accessible via APIs without restrictions. Proceeding anyway.
Nov 05 11:19:04 wyatt-aspiree1532 polkitd(authority=local)[600]: Operator of unix-session:1 successfully authenticated as unix-user:wyatt to gain ONE-SHOT authorization for action org.freedesktop.policykit.exec for unix-process:1188:12412 [/usr/bin/stacer] (owned by unix-user:wyatt)
Nov 05 11:19:04 wyatt-aspiree1532 pkexec[1377]: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Nov 05 11:19:04 wyatt-aspiree1532 pkexec[1377]: wyatt: Executing command [USER=root] [TTY=unknown] [CWD=/home/wyatt] [COMMAND=/usr/bin/rm -rf /var/cache/apt/archives/lock /var/log/auth.log /var/log/boot.log /var/log/btmp /var/log/cups /var/log/dmesg /var/log/dmesg.0 /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/monitorix /var/log/monitorix-httpd /var/log/private /var/log/syslog /var/log/unattended-upgrades /var/log/wtmp /var/log/Xorg.0.log /var/log/Xorg.0.log.old /home/wyatt/.cache/gstreamer-1.0 /home/wyatt/.cache/icon-cache.kcache /home/wyatt/.cache/lxqt-notificationd /home/wyatt/.cache/mesa_shader_cache /home/wyatt/.cache/openbox /home/wyatt/.cache/pcmanfm-qt /home/wyatt/.cache/thumbnails]
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Thread (pooled)[1191]: segfault at 20 ip 0000000000000020 sp 000078cb273ffc18 error 14 in stacer[57c04c6c7000+13a000] likely on CPU 0 (core 0, socket 0)
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Code: Unable to access opcode bytes at 0xfffffffffffffff6.
Nov 05 11:19:12 wyatt-aspiree1532 systemd[1]: Started crash report submission.
Nov 05 11:19:13 wyatt-aspiree1532 whoopsie[1424]: [11:19:12] Using lock path: /var/lock/whoopsie/lock
Nov 05 11:19:13 wyatt-aspiree1532 systemd[1]: whoopsie.service: Deactivated successfully.
Nov 05 11:19:16 wyatt-aspiree1532 systemd[1]: Started crash report submission.
Nov 05 11:19:16 wyatt-aspiree1532 whoopsie[1433]: [11:19:16] Using lock path: /var/lock/whoopsie/lock
Nov 05 11:19:16 wyatt-aspiree1532 systemd[1]: whoopsie.service: Deactivated successfully.
Nov 05 11:19:24 wyatt-aspiree1532 polkitd(authority=local)[600]: Operator of unix-session:1 successfully authenticated as unix-user:wyatt to gain ONE-SHOT authorization for action org.bleachbit for unix-process:1014:5051 [/usr/bin/lxqt-panel] (owned by unix-user:wyatt)
Nov 05 11:19:24 wyatt-aspiree1532 pkexec[1427]: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Nov 05 11:19:24 wyatt-aspiree1532 pkexec[1427]: wyatt: Executing command [USER=root] [TTY=unknown] [CWD=/home/wyatt] [COMMAND=/usr/bin/bleachbit]
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] AppArmor D-Bus mediation is enabled
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.portal.Desktop' requested by ':1.0' (uid=0 pid=1427 comm="/usr/bin/python3 /usr/bin/bleachbit " label="unconfined")
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.portal.Documents' requested by ':1.1' (uid=0 pid=1446 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.impl.portal.PermissionStore' requested by ':1.2' (uid=0 pid=1451 comm="/usr/libexec/xdg-document-portal " label="unconfined")
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.impl.portal.PermissionStore'
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.portal.Documents'
Nov 05 11:19:25 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.impl.portal.desktop.gtk' requested by ':1.1' (uid=0 pid=1446 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.gtk.vfs.Daemon' requested by ':1.4' (uid=0 pid=1466 comm="/usr/libexec/xdg-desktop-portal-gtk " label="unconfined")
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.gtk.vfs.Daemon'
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.impl.portal.desktop.gtk'
Nov 05 11:19:26 wyatt-aspiree1532 rtkit-daemon[937]: Supervising 6 threads of 3 processes of 1 users.
Nov 05 11:19:26 wyatt-aspiree1532 rtkit-daemon[937]: Supervising 6 threads of 3 processes of 1 users.
Nov 05 11:19:26 wyatt-aspiree1532 rtkit-daemon[937]: Supervising 6 threads of 3 processes of 1 users.
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.impl.portal.desktop.kde' requested by ':1.1' (uid=0 pid=1446 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
Nov 05 11:19:26 wyatt-aspiree1532 org.freedesktop.impl.portal.desktop.kde[1490]: QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
Nov 05 11:19:26 wyatt-aspiree1532 org.freedesktop.impl.portal.desktop.kde[1490]: QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.impl.portal.desktop.kde'
Nov 05 11:19:26 wyatt-aspiree1532 org.freedesktop.impl.portal.desktop.kde[1490]: xdp-kde: Desktop portal registered successfully
Nov 05 11:19:26 wyatt-aspiree1532 xdg-desktop-por[1446]: Failed connect to PipeWire: Couldn't connect to PipeWire
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Activating service name='org.freedesktop.secrets' requested by ':1.1' (uid=0 pid=1446 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
Nov 05 11:19:26 wyatt-aspiree1532 org.freedesktop.secrets[1496]: GNOME_KEYRING_CONTROL=/root/.cache/keyring-08KGW2
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.secrets'
Nov 05 11:19:26 wyatt-aspiree1532 dbus-daemon[1443]: [session uid=0 pid=1441] Successfully activated service 'org.freedesktop.portal.Desktop'
Nov 05 11:19:56 wyatt-aspiree1532 xdg-desktop-por[1446]: Failed to get application states: GDBus.Error:org.freedesktop.DBus.Error.UnknownInterface: No such interface 'org.freedesktop.impl.portal.Background' at object path '/org/freedesktop/portal/desktop'
Nov 05 11:21:35 wyatt-aspiree1532 wpa_supplicant[608]: wlp2s0: CTRL-EVENT-BEACON-LOSS
Nov 05 11:21:36 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Nov 05 11:21:36 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Nov 05 11:21:36 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
```

---

### Post by 1fallen on 2024-11-05
Will you include this please:
```
iw wlp2s0 get power_save 

```

---

### Post by wyattwhiteeagle on 2024-11-05
> **1fallen said:**
> Will you include this please:
```
iw wlp2s0 get power_save 

```
Power save: off

---

### Post by 1fallen on 2024-11-06
Well so much for that hunch. Thanks though for replying.

Was Bluetooh activated and in use at this time? Plus it would be nice to see your current kernel in use.

---

### Post by wyattwhiteeagle on 2024-11-06
> **1fallen said:**
> Plus it would be nice to see your current kernel in use.
uname -srm
```
Linux 6.8.0-48-generic x86_64
```
Is that the kernel?
I'm not certain but thats what came up with that command.

> **1fallen said:**
> Was Bluetooh activated and in use at this time?
I'm not certain if bluetooth was activated or not.
Is there a way to find out?

---

### Post by 1fallen on 2024-11-06
> **wyattwhiteeagle said:**
> uname -srm
```
Linux 6.8.0-48-generic x86_64
```
Is that the kernel?
Yep

> **wyattwhiteeagle said:**
> 
I'm not certain if bluetooth was activated or not.
Is there a way to find out?

Like this:
```
systemctl status bluetooth
```

There are many lines in journal logs that point to hardware faults
```
 wpa_supplicant[608]: wlp2s0: CTRL-EVENT-BEACON-LOSS
kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
kernel: ath: phy0: Chip reset failed
kernel: ath: phy0: Unable to reset channel, reset status -22

```

But this is very interesting:
```
wyatt: Executing command [USER=root] [TTY=unknown] [CWD=/home/wyatt] [COMMAND=/usr/bin/rm -rf /var/cache/apt/archives/lock /var/log/auth.log /var/log/boot.log /var/log/btmp /var/log/cups /var/log/dmesg /var/log/dmesg.0 /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/monitorix /var/log/monitorix-httpd /var/log/private /var/log/syslog /var/log/unattended-upgrades /var/log/wtmp /var/log/Xorg.0.log /var/log/Xorg.0.log.old /home/wyatt/.cache/gstreamer-1.0 /home/wyatt/.cache/icon-cache.kcache /home/wyatt/.cache/lxqt-notificationd /home/wyatt/.cache/mesa_shader_cache /home/wyatt/.cache/openbox /home/wyatt/.cache/pcmanfm-qt /home/wyatt/.cache/thumbnails]
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Thread (pooled)[1191]: segfault at 20 ip 0000000000000020 sp 000078cb273ffc18 error 14 in stacer[57c04c6c7000+13a000] likely on CPU 0 (core 0, socket 0)
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Code: Unable to access opcode bytes at 0xfffffffffffffff6.
Nov 05 11:19:12 wyatt-aspiree1532 systemd[1]: Started crash report submission.
```

Is it better today after your removal of the lock.file?

---

### Post by wyattwhiteeagle on 2024-11-06
> **1fallen said:**
> Like this:
```
systemctl status bluetooth
```
Yes...it's still the default settings for it.
Active: active (running) since Wed 2024-11-06 17:06:35 EST; 50min ago


> **1fallen said:**
> There are many lines in journal logs that point to hardware faults
```
 wpa_supplicant[608]: wlp2s0: CTRL-EVENT-BEACON-LOSS
kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
kernel: ath: phy0: Chip reset failed
kernel: ath: phy0: Unable to reset channel, reset status -22

```
How do I fix those?


> **1fallen said:**
> But this is very interesting:
```
wyatt: Executing command [USER=root] [TTY=unknown] [CWD=/home/wyatt] [COMMAND=/usr/bin/rm -rf /var/cache/apt/archives/lock /var/log/auth.log /var/log/boot.log /var/log/btmp /var/log/cups /var/log/dmesg /var/log/dmesg.0 /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/monitorix /var/log/monitorix-httpd /var/log/private /var/log/syslog /var/log/unattended-upgrades /var/log/wtmp /var/log/Xorg.0.log /var/log/Xorg.0.log.old /home/wyatt/.cache/gstreamer-1.0 /home/wyatt/.cache/icon-cache.kcache /home/wyatt/.cache/lxqt-notificationd /home/wyatt/.cache/mesa_shader_cache /home/wyatt/.cache/openbox /home/wyatt/.cache/pcmanfm-qt /home/wyatt/.cache/thumbnails]
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Thread (pooled)[1191]: segfault at 20 ip 0000000000000020 sp 000078cb273ffc18 error 14 in stacer[57c04c6c7000+13a000] likely on CPU 0 (core 0, socket 0)
Nov 05 11:19:11 wyatt-aspiree1532 kernel: Code: Unable to access opcode bytes at 0xfffffffffffffff6.
Nov 05 11:19:12 wyatt-aspiree1532 systemd[1]: Started crash report submission.
```


Is it better today after your removal of the lock.file?
The removal of all those files are an action done in either Stacer or Bleachbit.
With the very next line mentioning an error in stacer, my guess is its a command in stacer.
In stacer, I search for all that can be cleaned, then select all, then click to clean, put in the password, etc.


Sometimes it seems to run better, other times its like I'm doing nothing but rebooting repeatedly for an hour or so afterward.

---

### Post by 1fallen on 2024-11-06
> **wyattwhiteeagle said:**
> Yes...it's still the default settings for it.
Active: active (running) since Wed 2024-11-06 17:06:35 EST; 50min ago

If you don't use it disable it from auto starting:
```
systemctl disable bluetooth
```
If you ever need it just use this for a session only:
```
systemctl start --now bluetooth
```
Your next reboot won't start it until you tell it to.
> **wyattwhiteeagle said:**
> 
How do I fix those?
Try adding this to "/etc/default/grub" if you use grub as your bootloader.
```
intel_iommu=off
```
Then update grub
EDIT: Forgot to NOTE, This parameter seems to be only needed set to "on" when using advanced  Virtual Machine features like PCI pass-through, so disable it shouldn't  be a problem in most cases.
```
sudo update-grub
```
Use that parameter for while to see if it helps.


> **wyattwhiteeagle said:**
> 
The removal of all those files are an action done in either Stacer or Bleachbit.
With the very next line mentioning an error in stacer, my guess is its a command in stacer.
In stacer, I search for all that can be cleaned, then select all, then click to clean, put in the password, etc.

I just had to check, thanks for that info though.

---

### Post by wyattwhiteeagle on 2024-11-06
I did all that you suggested.
Hopefully the adversities have been minimized or dealt with.
I want to thank you for your help.
I plan to post back here in a couple days to maybe have a look at things.
Hope all goes well.

---

### Post by wyattwhiteeagle on 2024-11-07
This just happened again...3 times within 3 hours.

What all reports are needed and where do I put those reports?

System-Info
```
View at: https://paste.ubuntu.com/p/cbcbvn9MP6/
```
Wireless-Info
```
https://termbin.com/svgt
```

---

### Post by 1fallen on 2024-11-07
Please show this as well, I'm looking at the system-info now:
```
cat /proc/cmdline 

```
I just don't see this anywhere>>"intel_iommu=off"

---

### Post by wyattwhiteeagle on 2024-11-07
> **1fallen said:**
> Please show this as well, I'm looking at the system-info now:
```
cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-6.8.0-48-generic root=UUID=0c7113c2-298d-4acc-a6d4-57e50c9abf16 ro quiet splash vt.handoff=7
> **1fallen said:**
> I just don't see this anywhere>>"intel_iommu=off"
I know I put that line where you said put it and updated grub...let me check that file and make sure it's still there.

I put this at the very end of /etc/default/grub...
```
# Added via advice on ubuntuforums
# https://ubuntuforums.org/showthread.php?t=2502213
intel_iommu=off
```

---

### Post by 1fallen on 2024-11-07
It should look like this:
```
GRUB_CMDLINE_LINUX="intel_iommu=off"
```

---

### Post by wyattwhiteeagle on 2024-11-07
> **1fallen said:**
> It should look like this:
```
GRUB_CMDLINE_LINUX="intel_iommu=off"
```
> GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="intel_iommu=off" 
# Added via advice on ubuntuforums [https://ubuntuforums.org/showthread.php?t=2502213](https://ubuntuforums.org/showthread.php?t=2502213)
# intel_iommu=off

Is that ok?

---

### Post by 1fallen on 2024-11-07
Yep that's correct,
Don't forget to update-grub again.

---

### Post by wyattwhiteeagle on 2024-11-07
> **1fallen said:**
> Yep that's correct,
Don't forget to update-grub again.
grub updated and waiting to see how it goes.
Hopefully we see some good results.

---

### Post by wyattwhiteeagle on 2024-11-08
it happened yet again...

Do I need to run new reports?

---

### Post by 1fallen on 2024-11-08
> **wyattwhiteeagle said:**
> it happened yet again...
I hate when that happens, you can remove the"intel_iommu=off" from Grub 
> **wyattwhiteeagle said:**
> 
Do I need to run new reports?
Crash or sudden reboots are very hard to grab logs from, but we can look at a couple more:

```
cd /var/crash && ls
```

And let's check dmesg as well please:
```
dmesg | grep -i crash
```

This is almost looking like a hardware issue.

To rule out hardware, if possible use a different mouse and try to use a wired connection and disable WiFi.

---

### Post by wyattwhiteeagle on 2024-11-08
cd /var/crash && ls
```
_usr_bin_stacer.1000.crash
```
dmesg | grep -i crash
```
[   12.990727] pstore: Using crash dump compression: deflate
```
> **1fallen said:**
> To rule out hardware, if possible use a different mouse and try to use a wired connection and disable WiFi.
I wish I could say that were possible.

---

### Post by 1fallen on 2024-11-08
nothing else is popping out in any of your logs so far.

My friend I'm at a loss for any other suggestions....from what those two showed, I'm leaning more to hardware issues.

Or a corrupt install......is there anything when this all began that you installed recently, or changed???

---

### Post by wyattwhiteeagle on 2024-11-09
Is it power_save that disconnects the wifi when it goes idle?

You know, come to think about it, when I was looking at my list of what I install, brave browser has a security feature known as "keyring lock".
Also, When I was testing 24.04 Noble to see if I needed to revert back here to 22.04 Jammy, it seemed bleachbit caused this same issue.


This is only a thought, something inside brave browser, its keyring lock, bleachbit, or a combination of those...
Could something, especially in bleachbit, be causing some things to become unstable?
```
# Brave-Browser
# https://brave.com/linux/#release-channel-installation
   apt install -y curl
   curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
   echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|tee /etc/apt/sources.list.d/brave-browser-release.list
   apt update
   apt install -y brave-browser
```


Here's a list of what I install.
```
# Ubuntu-Restricted-Extras
# Wine-Staging
# Disk Usage Analyzer
# Monitorix
# Bleachbit
# Stacer
# DebOrphan
# Webcamoid
# Spotify
# Brave-Browser
# curl
# PsUtils
# lm-sensors
# KolourPaint
# Timeshift
# Fdupes
# Falkon
```

---

### Post by 1fallen on 2024-11-09
> **wyattwhiteeagle said:**
> Is it power_save that disconnects the wifi when it goes idle?
Yes it is. But you said it was set to off. Is that still correct?
> **wyattwhiteeagle said:**
> 
You know, come to think about it, when I was looking at my list of what I install, brave browser has a security feature known as "keyring lock".
Also, When I was testing 24.04 Noble to see if I needed to revert back here to 22.04 Jammy, it seemed bleachbit caused this same issue.

I run Brave on all my OS's with no Ill side effects.

Bleachbit can be a real showstopper, if the wrong things are removed, and very often irreversible.... 

I did notice Stacer also reported a Crash.....How Good are your back-ups?
What would be Ideal is if you had a Dated-Back-ups to restore from, I keep many snapshots when I'm mucking about with any of my systems.

---

### Post by wyattwhiteeagle on 2024-11-09
> **1fallen said:**
> Quote Originally Posted by wyattwhiteeagle [https://ubuntuforums.org/showthread.php?p=14212282#post14212282](https://ubuntuforums.org/showthread.php?p=14212282#post14212282)
Is it power_save that disconnects the wifi when it goes idle?
Yes it is. But you said it was set to off. Is that still correct?
Yes, that is still correct.
> **1fallen said:**
> Quote Originally Posted by wyattwhiteeagle [https://ubuntuforums.org/showthread.php?p=14212282#post14212282](https://ubuntuforums.org/showthread.php?p=14212282#post14212282)
You know, come to think about it, when I was looking at my list of what I install, brave browser has a security feature known as "keyring lock".
Also, When I was testing 24.04 Noble to see if I needed to revert back here to 22.04 Jammy, it seemed bleachbit caused this same issue.
I run Brave on all my OS's with no Ill side effects.
Ok, that means Brave isn't a contributor, unless I have brave configured improperly to my liking's.
> **1fallen said:**
> Bleachbit can be a real showstopper, if the wrong things are removed, and very often irreversible....
I did notice Stacer also reported a Crash.....
I've been meaning to extract from Bleachbit and Stacer what all locations they clean then not install bleachbit at all and use stacer only as a form of reference. I guess it's time to get that done.
> **1fallen said:**
> How Good are your back-ups?
What would be Ideal is if you had a Dated-Back-ups to restore from, I keep many snapshots when I'm mucking about with any of my systems.
The only thing close are Timeshift "restore points". No real back-ups.
Currently, I don't have any "restore points" in Timeshift.
Focal Fossa had something to where it would detect a flash drive UUID.
But after Focal Fossa, that was changed to where the system might not recognize the flash drive UUID when mounted to media.
Mounting to media seems to have become the standard for flash drive's.
Because of the flash drive probably not recognized by the system and being marked as "corrupt", I haven't been using rdiff-backup.
Past due time for me to look into correcting that issue as well.

---

### Post by 1fallen on 2024-11-09
Snapshots are only one part of good back-ups /home Data is important as well.

That's just for starters

---

