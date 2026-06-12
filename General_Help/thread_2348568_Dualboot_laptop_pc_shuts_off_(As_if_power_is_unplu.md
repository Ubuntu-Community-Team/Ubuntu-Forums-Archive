---
title: "Dualboot laptop pc shuts off (As if power is unplugged suddenly on a Desktop) while r"
date: 2017-01-04
forum: General Help
---

### Post by r4sh33d on 2017-01-04
I am very new to linux Operating Systems . I recently dual boot ubuntu 16.04 lts alongside windows 10 . but as soon as boot in to ubuntu , The pc will shut off as if The laptop battery is removed immediately. This usually happen 1 - 2 minutes after complete boot , at times it will shut off in the login screen. I tried ubuntu 14 and the behavior is even worse.I've updated The software through software updater and i still have the same issue. I think its not an hardware problem because i never experience that behavior on windows 10 even when the pc is very very hot. please help. i have copied some log from an app called 'syslog'.
i was able to trace the last message before  the pc shut off and it is :

```
Jan  4 20:49:01 R4SH33D-PC thermald[828]: critical temp reached
```
my laptop specs are  celeron 2.16ghz , 4gb ram .

The rest of the log is :
`  
```
Jan  4 20:48:11 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to 00:18:25:12:d1:70 completed [id=0 id_str=]
Jan  4 20:48:12 R4SH33D-PC NetworkManager[862]: <info>  [1483580892.0777] device (wlp2s0): supplicant interface state: associating -> completed
Jan  4 20:48:12 R4SH33D-PC NetworkManager[862]: <info>  [1483580892.0778] device (wlp2s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SOCIAL SCIENCES'.
Jan  4 20:48:12 R4SH33D-PC NetworkManager[862]: <info>  [1483580892.0780] device (wlp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Jan  4 20:48:12 R4SH33D-PC dbus[843]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Jan  4 20:48:12 R4SH33D-PC NetworkManager[862]: <info>  [1483580892.1155] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
Jan  4 20:48:12 R4SH33D-PC systemd[1]: Starting Locale Service...
Jan  4 20:48:12 R4SH33D-PC gnome-session[1614]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jan  4 20:48:12 R4SH33D-PC gnome-session[1614]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jan  4 20:48:12 R4SH33D-PC NetworkManager[862]: <info>  [1483580892.2745] dhcp4 (wlp2s0): dhclient started with pid 1736
Jan  4 20:48:12 R4SH33D-PC gnome-session[1614]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jan  4 20:48:12 R4SH33D-PC dbus[843]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan  4 20:48:12 R4SH33D-PC systemd[1]: Started Locale Service.
Jan  4 20:48:12 R4SH33D-PC dhclient[1736]: DHCPREQUEST of 10.91.3.92 on wlp2s0 to 255.255.255.255 port 67 (xid=0x3ae2cd5d)
Jan  4 20:48:12 R4SH33D-PC gnome-session-binary[1614]: Entering running state
Jan  4 20:48:13 R4SH33D-PC gnome-session[1614]: (process:1774): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Jan  4 20:48:13 R4SH33D-PC gnome-session[1614]: (process:1774): indicator-application-service-WARNING **: Name Lost
Jan  4 20:48:13 R4SH33D-PC dbus[843]: [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
Jan  4 20:48:13 R4SH33D-PC systemd[1]: Starting Disk Manager...
Jan  4 20:48:13 R4SH33D-PC avahi-daemon[829]: Joining mDNS multicast group on interface wlp2s0.IPv6 with address fe80::412:7a1:4a0b:fd76.
Jan  4 20:48:13 R4SH33D-PC avahi-daemon[829]: New relevant interface wlp2s0.IPv6 for mDNS.
Jan  4 20:48:13 R4SH33D-PC avahi-daemon[829]: Registering new address record for fe80::412:7a1:4a0b:fd76 on wlp2s0.*.
Jan  4 20:48:14 R4SH33D-PC udisksd[1803]: udisks daemon version 2.1.7 starting
Jan  4 20:48:14 R4SH33D-PC dbus[843]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jan  4 20:48:14 R4SH33D-PC systemd[1]: Started Disk Manager.
Jan  4 20:48:14 R4SH33D-PC udisksd[1803]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jan  4 20:48:14 R4SH33D-PC gnome-session[1614]: (gnome-software:1761): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Jan  4 20:48:14 R4SH33D-PC gnome-session[1614]: (gnome-software:1761): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Jan  4 20:48:14 R4SH33D-PC dbus[843]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Jan  4 20:48:14 R4SH33D-PC org.gtk.vfs.AfcVolumeMonitor[1474]: Volume monitor alive
Jan  4 20:48:16 R4SH33D-PC dhclient[1736]: DHCPREQUEST of 10.91.3.92 on wlp2s0 to 255.255.255.255 port 67 (xid=0x3ae2cd5d)
Jan  4 20:48:17 R4SH33D-PC gnome-session[1614]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jan  4 20:48:18 R4SH33D-PC org.freedesktop.fwupd[843]: (fwupd:1820): Fu-WARNING **: Failed to coldplug: UEFI firmware updating not supported
Jan  4 20:48:18 R4SH33D-PC dbus[843]: [system] Successfully activated service 'org.freedesktop.fwupd'
Jan  4 20:48:20 R4SH33D-PC gnome-session[1614]: ** (unity-fallback-mount-helper:1756): WARNING **: Can't call IsLocked() on the Unity.Session object: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'com.canonical.Unity.Session' on object at path /com/canonical/Unity/Session
Jan  4 20:48:20 R4SH33D-PC org.gnome.ScreenSaver[1474]: ** Message: Lost the name, shutting down.
Jan  4 20:48:23 R4SH33D-PC dhclient[1736]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x598d5501)
Jan  4 20:48:26 R4SH33D-PC dhclient[1736]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 5 (xid=0x598d5501)
Jan  4 20:48:27 R4SH33D-PC bluetoothd[890]: Endpoint unregistered: sender=:1.41 path=/MediaEndpoint/A2DPSource
Jan  4 20:48:27 R4SH33D-PC bluetoothd[890]: Endpoint unregistered: sender=:1.41 path=/MediaEndpoint/A2DPSink
Jan  4 20:48:29 R4SH33D-PC systemd[1]: Starting Stop ureadahead data collection...
Jan  4 20:48:29 R4SH33D-PC systemd[1]: Stopped Read required files in advance.
Jan  4 20:48:29 R4SH33D-PC systemd[1]: Started Stop ureadahead data collection.
Jan  4 20:48:31 R4SH33D-PC com.canonical.Unity.Scope.Applications[1474]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Jan  4 20:48:31 R4SH33D-PC com.canonical.Unity.Scope.Applications[1474]: (unity-scope-loader:1961): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Jan  4 20:48:31 R4SH33D-PC dhclient[1736]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x598d5501)
Jan  4 20:48:32 R4SH33D-PC gnome-session[1614]: ** (zeitgeist-datahub:2008): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Jan  4 20:48:37 R4SH33D-PC dbus[843]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jan  4 20:48:37 R4SH33D-PC systemd[1]: Starting Hostname Service...
Jan  4 20:48:37 R4SH33D-PC dbus[843]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan  4 20:48:37 R4SH33D-PC systemd[1]: Started Hostname Service.
Jan  4 20:48:41 R4SH33D-PC org.gtk.vfs.Daemon[1474]: ** (gvfsd:1546): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan  4 20:48:41 R4SH33D-PC org.gtk.vfs.Daemon[1474]: ** (process:2060): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan  4 20:48:41 R4SH33D-PC org.gtk.vfs.Daemon[1474]: ** (gvfsd:1546): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan  4 20:48:41 R4SH33D-PC org.gtk.vfs.Daemon[1474]: ** (process:2067): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan  4 20:48:41 R4SH33D-PC dhclient[1736]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x598d5501)
Jan  4 20:48:57 R4SH33D-PC dhclient[1736]: DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 7 (xid=0x598d5501)
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <warn>  [1483580937.5418] dhcp4 (wlp2s0): request timed out
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5419] dhcp4 (wlp2s0): state changed unknown -> timeout
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5587] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 1736
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5588] dhcp4 (wlp2s0): state changed timeout -> done
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5594] device (wlp2s0): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5598] manager: NetworkManager state is now DISCONNECTED
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <warn>  [1483580937.5609] device (wlp2s0): Activation: failed for connection 'SOCIAL SCIENCES'
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5621] device (wlp2s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  4 20:48:57 R4SH33D-PC avahi-daemon[829]: Withdrawing address record for fe80::412:7a1:4a0b:fd76 on wlp2s0.
Jan  4 20:48:57 R4SH33D-PC avahi-daemon[829]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::412:7a1:4a0b:fd76.
Jan  4 20:48:57 R4SH33D-PC avahi-daemon[829]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5755] policy: auto-activating connection 'SOCIAL SCIENCES'
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5788] device (wlp2s0): Activation: starting connection 'SOCIAL SCIENCES' (8e2c955d-e7eb-40ee-81ee-1d4b94c074f6)
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5792] device (wlp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5795] manager: NetworkManager state is now CONNECTING
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5806] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5811] device (wlp2s0): Activation: (wifi) connection 'SOCIAL SCIENCES' requires no security.  No secrets needed.
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5813] Config: added 'ssid' value 'SOCIAL SCIENCES'
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5813] Config: added 'scan_ssid' value '1'
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.5813] Config: added 'key_mgmt' value 'NONE'
Jan  4 20:48:57 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=00:18:25:12:d1:70 reason=3 locally_generated=1
Jan  4 20:48:57 R4SH33D-PC wpa_supplicant[1043]: nl80211: Was expecting local disconnect but got another disconnect event first
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112792] cfg80211: World regulatory domain updated:
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112801] cfg80211:  DFS Master region: unset
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112804] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112809] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112812] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112815] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112818] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112822] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112825] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112828] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC kernel: [  101.112830] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Jan  4 20:48:57 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <warn>  [1483580937.6217] sup-iface[0xfaf970,wlp2s0]: connection disconnected (reason -3)
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.6235] device (wlp2s0): supplicant interface state: completed -> disconnected
Jan  4 20:48:57 R4SH33D-PC NetworkManager[862]: <info>  [1483580937.6254] sup-iface[0xfaf970,wlp2s0]: config: set interface ap_scan to 1
Jan  4 20:48:57 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: Reject scan trigger since one is already pending
Jan  4 20:48:57 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: Failed to initiate AP scan
Jan  4 20:48:58 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: Trying to associate with 00:18:25:12:d1:70 (SSID='SOCIAL SCIENCES' freq=2417 MHz)
Jan  4 20:48:58 R4SH33D-PC NetworkManager[862]: <info>  [1483580938.4142] device (wlp2s0): supplicant interface state: disconnected -> associating
Jan  4 20:48:58 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-ASSOC-REJECT bssid=00:18:25:12:d1:70 status_code=16
Jan  4 20:48:58 R4SH33D-PC NetworkManager[862]: <info>  [1483580938.4539] device (wlp2s0): supplicant interface state: associating -> disconnected
Jan  4 20:48:58 R4SH33D-PC NetworkManager[862]: <info>  [1483580938.5542] device (wlp2s0): supplicant interface state: disconnected -> scanning
Jan  4 20:48:59 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Jan  4 20:48:59 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: Trying to associate with 00:18:25:12:d1:70 (SSID='SOCIAL SCIENCES' freq=2417 MHz)
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.2987] device (wlp2s0): supplicant interface state: scanning -> associating
Jan  4 20:48:59 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: Associated with 00:18:25:12:d1:70
Jan  4 20:48:59 R4SH33D-PC wpa_supplicant[1043]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to 00:18:25:12:d1:70 completed [id=0 id_str=]
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.3429] device (wlp2s0): supplicant interface state: associating -> completed
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.3431] device (wlp2s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SOCIAL SCIENCES'.
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.3438] device (wlp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.3446] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
Jan  4 20:48:59 R4SH33D-PC NetworkManager[862]: <info>  [1483580939.3565] dhcp4 (wlp2s0): dhclient started with pid 2180
Jan  4 20:48:59 R4SH33D-PC dhclient[2180]: DHCPREQUEST of 10.91.3.92 on wlp2s0 to 255.255.255.255 port 67 (xid=0x36cfb382)
Jan  4 20:49:01 R4SH33D-PC avahi-daemon[829]: Joining mDNS multicast group on interface wlp2s0.IPv6 with address fe80::412:7a1:4a0b:fd76.
Jan  4 20:49:01 R4SH33D-PC avahi-daemon[829]: New relevant interface wlp2s0.IPv6 for mDNS.
Jan  4 20:49:01 R4SH33D-PC avahi-daemon[829]: Registering new address record for fe80::412:7a1:4a0b:fd76 on wlp2s0.*.
**Jan  4 20:49:01 R4SH33D-PC thermald[828]: critical temp reached**
Jan  4 21:07:07 R4SH33D-PC rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="828" x-info="http://www.rsyslog.com"] start
Jan  4 21:07:07 R4SH33D-PC systemd-modules-load[201]: Inserted module 'lp'
Jan  4 21:07:07 R4SH33D-PC rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try [http://www.rsyslog.com/e/2222](http://www.rsyslog.com/e/2222) ]
Jan  4 21:07:07 R4SH33D-PC rsyslogd: rsyslogd's groupid changed to 108
Jan  4 21:07:07 R4SH33D-PC rsyslogd: rsyslogd's userid changed to 104
Jan  4 21:07:07 R4SH33D-PC systemd-modules-load[201]: Inserted module 'ppdev'
Jan  4 21:07:07 R4SH33D-PC systemd-modules-load[201]: Inserted module 'parport_pc'
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Apply Kernel Variables.
Jan  4 21:07:07 R4SH33D-PC loadkeys[206]: Loading /etc/console-setup/cached.kmap.gz
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Set console keymap.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Create Static Device Nodes in /dev.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting udev Kernel Device Manager...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started udev Kernel Device Manager.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Remount Root and Kernel File Systems...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Remount Root and Kernel File Systems.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Reached target Local File Systems (Pre).
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting udev Coldplug all Devices...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Flush Journal to Persistent Storage...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Load/Save Random Seed...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Reached target Local File Systems.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting LSB: AppArmor initialization...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Set console font and keymap...
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Clean up any mess left by 0dns-up...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Linux version 4.4.0-57-generic (buildd@lgw01-54) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 (Ubuntu 4.4.0-57.78-generic 4.4.35)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-57-generic root=UUID=c4ba630d-e550-421d-a54e-36388cc7c6b1 ro quiet splash vt.handoff=7
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Load/Save Random Seed.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] KERNEL supported cpus:
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   Intel GenuineIntel
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   AMD AuthenticAMD
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   Centaur CentaurHauls
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Flush Journal to Persistent Storage.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Create Volatile Files and Directories...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000007a9a7fff] usable
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007a9a8000-0x000000007ada7fff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007ada8000-0x000000007afa7fff] ACPI NVS
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007afa8000-0x000000007afe7fff] ACPI data
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007afe8000-0x000000007bffffff] usable
Jan  4 21:07:07 R4SH33D-PC systemd-tmpfiles[301]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007c000000-0x000000007c7fffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x000000007ca00000-0x000000007fffffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fea00000-0x00000000feafffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started udev Coldplug all Devices.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed03000-0x00000000fed03fff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed09fff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1cfff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fedbffff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Show Plymouth Boot Screen...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000017fffffff] usable
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] SMBIOS 2.8 present.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] DMI: Hewlett-Packard HP 250 G4 Notebook PC/80C5, BIOS F.0B 06/04/2015
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Clean up any mess left by 0dns-up.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] e820: last_pfn = 0x180000 max_arch_pfn = 0x400000000
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] MTRR default type: uncachable
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   00000-9FFFF write-back
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Nameserver information manager...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   C0000-FFFFF write-protect
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] MTRR variable ranges enabled:
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   1 base 0FFA00000 mask FFFE00000 write-protect
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   2 base 000000000 mask F80000000 write-back
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Nameserver information manager.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   3 base 07C000000 mask FFC000000 uncachable
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Created slice system-systemd\x2dbacklight.slice.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   4 base 100000000 mask F80000000 write-back
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   5 disabled
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   6 disabled
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000]   7 disabled
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] e820: last_pfn = 0x7c000 max_arch_pfn = 0x400000000
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Show Plymouth Boot Screen.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220a000, 0x0220afff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220b000, 0x0220bfff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220c000, 0x0220cfff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220d000, 0x0220dfff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220e000, 0x0220efff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] BRK [0x0220f000, 0x0220ffff] PGTABLE
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] RAMDISK: [mem 0x33814000-0x35c01fff]
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 HPQOEM)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: XSDT 0x000000007AFE7120 000084 (v01 HPQOEM SLIC-MPC 00000003 HP   01000013)
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Create Volatile Files and Directories.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: FACP 0x000000007AFDC000 00010C (v05 HPQOEM SLIC-MPC 00000003 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: DSDT 0x000000007AFCF000 009E52 (v02 HPQOEM SLIC-MPC 00000003 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: FACS 0x000000007AFA3000 000040
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: UEFI 0x000000007AFE6000 000236 (v01 HPQOEM INSYDE   00000001 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Update UTMP about System Boot/Shutdown...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: UEFI 0x000000007AFE4000 000042 (v01 HPQOEM INSYDE   00000000 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFDD000 006687 (v01 HPQOEM INSYDE   00001000 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Starting Network Time Synchronization...
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: MCFG 0x000000007AFDA000 00003C (v01 HPQOEM INSYDE   00000003 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFD9000 0005F4 (v01 HPQOEM CpuDptf  00000003 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFCE000 0009F8 (v01 HPQOEM DptfTab  00000003 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFCD000 000763 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFCC000 000290 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC systemd[1]: Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: SSDT 0x000000007AFCB000 00017A (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: APIC 0x000000007AFDB000 000084 (v03 HPQOEM SLIC-MPC 00000003 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: FPDT 0x000000007AFCA000 000044 (v01 HPQOEM SLIC-MPC 00000002 HP   00040000)
Jan  4 21:07:07 R4SH33D-PC kernel: [    0.000000] ACPI: Local APIC address 0xfee00000`
```

---

### Post by QIII on 2017-01-04
Hello!

When posting output from the terminal, please use code tags:

1.  Click the # button above the text input box, place your cursor between the code tags and paste or type your text.
2.  Paste or type your text, highlight it and click the # button.
3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Despite the fact that you do not believe your problem to be hardware, it most certainly is.  Your first line from the terminal indicates that.  Your machine should *never* get "very, very hot" whether it is running Windows or Ubuntu.  Just a fraction of a degree may mean the difference in thermal shutdown conditions.

What is the manufacturer and model of your laptop?  Some manufacturers defer temperature control to the OS -- and OS almost always means Windows.

---

### Post by r4sh33d on 2017-01-05
Thanks for your reply sir .
The model is  .. Hp 250 g4 ..

---

