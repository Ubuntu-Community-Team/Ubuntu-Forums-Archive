---
title: "Ubuntu 16.04 Hangs on Shut Down"
date: 2017-05-04
forum: General Help
---

### Post by Alan_Luu on 2017-05-04
I recently tried to install Ubuntu 16.04 alongside Windows 10 on my New ASUS Zenbook Pro, and it works fine for the most part, but whenever I try to shutdown it gets stuck at a black screen with the lines:

> 
/dev/nvme0n1p5: clean, 229556/14327800 files, 2135513/57280768 blocks


and sometimes

>  
sd 3:0:0:0: [sda] No Caching mode page found
sd 3:0:0:0: [sda] Assuming drive cache: write through


I checked the system log at the time of shutdown, and it says

> May  4 10:30:40 alan-N501VW anacron[855]: Job `cron.daily' started
May  4 10:30:40 alan-N501VW anacron[3473]: Updated timestamp for job `cron.daily' to 2017-05-04
May  4 10:30:40 alan-N501VW gnome-session[1685]: gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May  4 10:30:40 alan-N501VW gnome-session[1685]: message repeated 2 times: [ gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
May  4 10:30:40 alan-N501VW gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May  4 10:30:40 alan-N501VW gnome-session-binary[1685]: message repeated 2 times: [ GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
May  4 10:30:40 alan-N501VW gnome-session[1685]: gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May  4 10:30:40 alan-N501VW gnome-session[1685]: message repeated 2 times: [ gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
May  4 10:30:40 alan-N501VW gnome-session-binary[1685]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May  4 10:30:40 alan-N501VW gnome-session-binary[1685]: message repeated 2 times: [ GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
May  4 10:30:40 alan-N501VW cracklib: no dictionary update necessary.
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Save/Restore Sound Card State...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Authenticate and Authorize Users to Run Privileged Tasks...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Disk Manager...
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Timers.
May  4 10:30:40 alan-N501VW systemd[1]: Stopped Daily apt activities.
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Sound Card.
May  4 10:30:40 alan-N501VW systemd[1]: Stopping ACPI event daemon...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Daemon for power management...
May  4 10:30:40 alan-N501VW systemd[1]: Stopped Timer to automatically refresh installed snaps.
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Bluetooth.
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Bluetooth service...
May  4 10:30:40 alan-N501VW bluetoothd[798]: Terminating
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Session c2 of user alan.
May  4 10:30:40 alan-N501VW systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
May  4 10:30:40 alan-N501VW /usr/lib/snapd/snapd[785]: main.go:67: Exiting on terminated signal.
May  4 10:30:40 alan-N501VW thermald[787]: Terminating ...
May  4 10:30:40 alan-N501VW snapd[785]: 2017/05/04 10:30:40.277977 main.go:67: Exiting on terminated signal.
May  4 10:30:40 alan-N501VW systemd[1]: Stopped Daily Cleanup of Temporary Directories.
May  4 10:30:40 alan-N501VW bluetoothd[798]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSource
May  4 10:30:40 alan-N501VW systemd[1]: Stopping User Manager for UID 1000...
May  4 10:30:40 alan-N501VW bluetoothd[798]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSink
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Manage, Install and Generate Color Profiles...
May  4 10:30:40 alan-N501VW ModemManager[793]: <info>  Caught signal, shutting down...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
May  4 10:30:40 alan-N501VW ModemManager[793]: <info>  ModemManager is shut down
May  4 10:30:40 alan-N501VW systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Graphical Interface.
May  4 10:30:40 alan-N501VW bluetoothd[798]: Stopping SDP server
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Light Display Manager...
May  4 10:30:40 alan-N501VW bluetoothd[798]: Exit
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Multi-User System.
May  4 10:30:40 alan-N501VW dbus[803]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Run anacron jobs...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Modem Manager...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Regular background program processing daemon...
May  4 10:30:40 alan-N501VW systemd[1]: Stopped target Login Prompts.
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Getty on tty1...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping LSB: daemon to balance interrupts for SMP systems...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Snappy daemon...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping System Logging Service...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Thermal Daemon Service...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping crash report submission daemon...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Make remote CUPS printers available locally...
May  4 10:30:40 alan-N501VW systemd[1246]: Reached target Shutdown.
May  4 10:30:40 alan-N501VW systemd[1246]: Starting Exit the Session...
May  4 10:30:40 alan-N501VW systemd[1246]: Stopped target Default.
May  4 10:30:40 alan-N501VW systemd[1246]: Stopped target Basic System.
May  4 10:30:40 alan-N501VW systemd[1246]: Stopped target Timers.
May  4 10:30:40 alan-N501VW systemd[1246]: Stopped target Paths.
May  4 10:30:40 alan-N501VW systemd[1246]: Stopped target Sockets.
May  4 10:30:40 alan-N501VW systemd[1]: Stopping LSB: Set the CPU Frequency Scaling governor to "ondemand"...
May  4 10:30:40 alan-N501VW systemd[1246]: Received SIGRTMIN+24 from PID 3567 (kill).
May  4 10:30:40 alan-N501VW systemd[1]: Stopping LSB: Speech Dispatcher...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping Accounts Service...
May  4 10:30:40 alan-N501VW NetworkManager[871]: <warn>  [1493911840.2904] error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: Authorization check failed: Message recipient disconnected from message bus without replying
May  4 10:30:40 alan-N501VW systemd[1]: Stopping LSB: automatic crash report generation...
May  4 10:30:40 alan-N501VW systemd[1]: Stopping LSB: Record successful boot for GRUB...
May  4 10:30:40 alan-N501VW rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="857" x-info="http://www.rsyslog.com"] exiting on signal 15.

I've tried things that other threads have suggested, changing settings in grub to

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

and changing system.conf settings:

> DefaultTimeoutStartSec=10s
DefaultTimeoutStoptSec=10s

but nothing seems to fix it. They just seem to change the lines that I see while hanging at the shutdown.

Does anyone know what's going on?

---

