---
title: "OMG Linux Froze + Crashed!!"
date: 2017-12-05
forum: General Help
---

### Post by frappe792 on 2017-12-05
Hi all,

Still fairly new to Linux......I can't believe it crashed on me tonight. I never thought it was possible. I was brainwashed to think it couldn't crash!! I actually think it's been over 2 years since I last saw a crash like this in Windows 7.

Any back to the indestructable Linux  .....   even the xkill command wouldn't even work (i'd setup a shortcut for it)

I was watching a video via Kodi and surfing webpages on my other screen.... and all of the sudden video stopped, I could still hear the audio. Webpage went completely white. Mouse could still move but did nothing. CTRL-ESC did nothing. No response from bluetooth keyboard or laptop keyboard.

I forced it shut holding down the power key. Started up again and seems back to normal.

Curious if anyone can pin point the problem to help me, I will paste a snippet (last 2-3 minutes of syslog) - any ideas?


```
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3118
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3112
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3118
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3112
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3321
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3321
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3327
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3327
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3085
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3101
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3139
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3133
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3499
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3505
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3047
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3041
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3079
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3073
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3499
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: qt.svg: <input>:663: Could not resolve property: radialGradient3505
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/trash.so' from launcher.
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/trash.so'
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
Dec  5 23:10:10 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/trash.so' from launcher.
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/trash.so'
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
Dec  5 23:10:11 myname-PORTEGE-R835 PackageKit: get-updates transaction /1074_bacebdee from uid 1000 finished with success after 1266ms
Dec  5 23:10:11 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: BluezQt: PendingCall Error: "Failed to activate service 'org.bluez': timed out"
Dec  5 23:10:11 myname-PORTEGE-R835 pulseaudio[2022]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Dec  5 23:10:12 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QQuickItem::stackAfter: Cannot stack after 0x555e65a99c00, which must be a sibling
Dec  5 23:10:12 myname-PORTEGE-R835 dbus[566]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Dec  5 23:10:12 myname-PORTEGE-R835 dbus[566]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Dec  5 23:10:12 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QQuickItem::stackAfter: Cannot stack after 0x555e65a99c00, which must be a sibling
Dec  5 23:10:12 myname-PORTEGE-R835 org.blueman.Mechanism[566]: Unable to init server: Could not connect: Connection refused
Dec  5 23:10:12 myname-PORTEGE-R835 org.blueman.Mechanism[566]: Unable to init server: Could not connect: Connection refused
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechanism: Starting blueman-mechanism
Dec  5 23:10:12 myname-PORTEGE-R835 dbus[566]: [system] Successfully activated service 'org.blueman.Mechanism'
Dec  5 23:10:12 myname-PORTEGE-R835 PackageKit: get-updates transaction /1075_bcdbbbbd from uid 1000 finished with success after 932ms
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechani[2665]: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechanism: loading Rfcomm
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechanism: loading RfKill
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechanism: loading Ppp
Dec  5 23:10:12 myname-PORTEGE-R835 blueman-mechanism: loading Network
Dec  5 23:10:14 myname-PORTEGE-R835 Dropbox[2194]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:10:14 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:10:14 myname-PORTEGE-R835 systemd-timesyncd[406]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
Dec  5 23:10:14 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: log_klipper: Failed to save history. Clipboard history cannot be saved.
Dec  5 23:10:19 myname-PORTEGE-R835 kernel: [   39.415261] logitech-hidpp-device 0003:046D:4055.0005: HID++ 4.5 device connected.
Dec  5 23:10:20 myname-PORTEGE-R835 upowerd[1075]: treating change event as add on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/0003:046D:C52B.0003/0003:046D:4055.0005/power_supply/hidpp_battery_1
Dec  5 23:10:20 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QObject::connect: invalid null parameter
Dec  5 23:10:20 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QObject::connect: invalid null parameter
Dec  5 23:10:21 myname-PORTEGE-R835 Dropbox[2194]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:10:21 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:10:22 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 16660, resource id: 83886135, major code: 18 (ChangeProperty), minor code: 0
Dec  5 23:10:22 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: PID 2333 terminated.
Dec  5 23:10:25 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXT_EXEC '/usr/bin/env' from launcher.
Dec  5 23:10:25 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/bin/env'
Dec  5 23:10:25 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 17721, resource id: 83886080, major code: 18 (ChangeProperty), minor code: 0
Dec  5 23:10:25 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 17725, resource id: 83886081, major code: 18 (ChangeProperty), minor code: 0
Dec  5 23:10:26 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: trying to show an empty dialog
Dec  5 23:10:29 myname-PORTEGE-R835 kernel: [   49.478225] audit: type=1400 audit(1512477629.951:53): apparmor="DENIED" operation="exec" profile="snap.chromium.chromium" name="/usr/bin/xdg-settings" pid=2831 comm="chromium-browse" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Dec  5 23:10:30 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: ATTENTION: default value of option force_s3tc_enable overridden by environment.
Dec  5 23:10:30 myname-PORTEGE-R835 dbus-daemon[1703]: Activating service name='org.kde.kwalletd5'
Dec  5 23:10:30 myname-PORTEGE-R835 dbus-daemon[1703]: Successfully activated service 'org.kde.kwalletd5'
Dec  5 23:10:30 myname-PORTEGE-R835 dbus[1703]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/modules/kwalletd5" interface="org.kde.KWallet" member="isEnabled" mask="send" name="org.kde.kwalletd5" pid=2691 label="snap.chromium.chromium" peer_pid=2844 peer_label="unconfined"
Dec  5 23:10:30 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2840:1205/231030.817938:ERROR:object_proxy.cc(574)] Failed to call method: org.kde.KWallet.isEnabled: object_path= /modules/kwalletd5: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.95" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.kde.KWallet" member="isEnabled" error name="(unset)" requested_reply="0" destination="org.kde.kwalletd5" (uid=1000 pid=2844 comm="/usr/bin/kwalletd5 ")
Dec  5 23:10:30 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2840:1205/231030.817967:ERROR:kwallet_dbus.cc(100)] Error contacting kwalletd5 (isEnabled)
Dec  5 23:10:30 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2840:1205/231030.819656:ERROR:object_proxy.cc(574)] Failed to call method: org.kde.KLauncher.start_service_by_desktop_name: object_path= /KLauncher: org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.klauncher was not provided by any .service files
Dec  5 23:10:30 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2840:1205/231030.819685:ERROR:kwallet_dbus.cc(72)] Error contacting klauncher to start kwalletd5
Dec  5 23:10:31 myname-PORTEGE-R835 kernel: [   50.894150] audit: type=1400 audit(1512477631.365:54): apparmor="DENIED" operation="exec" profile="snap.chromium.chromium" name="/usr/bin/xdg-settings" pid=2859 comm="TaskSchedulerBa" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Dec  5 23:10:32 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 2 (BadValue), sequence: 5111, resource id: 111149057, major code: 142 (Unknown), minor code: 3
Dec  5 23:10:33 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2842:1205/231033.390225:ERROR:object_proxy.cc(574)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.113" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=661 comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  5 23:10:33 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2842:1205/231033.390254:ERROR:networking_private_linux.cc(725)] Failed to enumerate network devices
Dec  5 23:10:33 myname-PORTEGE-R835 kernel: [   52.919919] audit: type=1107 audit(1512477633.390:55): pid=566 uid=105 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.NetworkManager" member="GetDevices" mask="send" name="org.freedesktop.NetworkManager" pid=2691 label="snap.chromium.chromium" peer_pid=661 peer_label="unconfined"
Dec  5 23:10:33 myname-PORTEGE-R835 kernel: [   52.919919]  exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=? terminal=?'
Dec  5 23:10:35 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2995:1205/231035.905420:ERROR:object_proxy.cc(574)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.114" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=661 comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  5 23:10:35 myname-PORTEGE-R835 kernel: [   55.436456] audit: type=1107 audit(1512477635.905:56): pid=566 uid=105 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.NetworkManager" member="GetDevices" mask="send" name="org.freedesktop.NetworkManager" pid=2691 label="snap.chromium.chromium" peer_pid=661 peer_label="unconfined"
Dec  5 23:10:35 myname-PORTEGE-R835 kernel: [   55.436456]  exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=? terminal=?'
Dec  5 23:10:37 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: /usr/lib/python3/dist-packages/blueman/plugins/applet/AppIndicator.py:8: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
Dec  5 23:10:37 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]:   from gi.repository import AppIndicator3 as girAppIndicator
Dec  5 23:10:37 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: ERROR:dbus.proxies:Introspect error on org.bluez:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Dec  5 23:10:37 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: ERROR:dbus.proxies:Introspect error on org.bluez:/org/bluez: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Dec  5 23:10:37 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: ERROR:dbus.proxies:Introspect error on org.bluez:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Dec  5 23:10:40 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2995:1205/231040.488626:ERROR:object_proxy.cc(574)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.115" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=661 comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  5 23:10:40 myname-PORTEGE-R835 kernel: [   60.021036] audit: type=1107 audit(1512477640.488:57): pid=566 uid=105 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.NetworkManager" member="GetDevices" mask="send" name="org.freedesktop.NetworkManager" pid=2691 label="snap.chromium.chromium" peer_pid=661 peer_label="unconfined"
Dec  5 23:10:40 myname-PORTEGE-R835 kernel: [   60.021036]  exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=? terminal=?'
Dec  5 23:10:42 myname-PORTEGE-R835 kernel: [   61.589308] audit: type=1400 audit(1512477642.056:58): apparmor="DENIED" operation="open" profile="snap.chromium.chromium" name="/run/udev/data/c240:0" pid=2691 comm="TaskSchedulerFo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Dec  5 23:10:42 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2841:1205/231042.093758:ERROR:udev_watcher.cc(60)] Failed to begin udev enumeration.
Dec  5 23:10:42 myname-PORTEGE-R835 blueman-mechanism: Exiting
Dec  5 23:10:45 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: Got EXT_EXEC '/usr/bin/gksu' from launcher.
Dec  5 23:10:45 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: kdeinit5: preparing to launch '/usr/bin/gksu'
Dec  5 23:10:45 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 31060, resource id: 119537664, major code: 18 (ChangeProperty), minor code: 0
Dec  5 23:10:45 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 31064, resource id: 119537665, major code: 18 (ChangeProperty), minor code: 0
Dec  5 23:10:49 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: Initializing nautilus-dropbox 2015.10.28
Dec  5 23:10:50 myname-PORTEGE-R835 dbus[566]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec  5 23:10:50 myname-PORTEGE-R835 systemd[1]: Starting Hostname Service...
Dec  5 23:10:50 myname-PORTEGE-R835 dbus[566]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  5 23:10:50 myname-PORTEGE-R835 systemd[1]: Started Hostname Service.
Dec  5 23:11:01 myname-PORTEGE-R835 dbus[1703]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/modules/kwalletd5" interface="org.kde.KWallet" member="isEnabled" mask="send" name="org.kde.kwalletd5" pid=2691 label="snap.chromium.chromium" peer_pid=2844 peer_label="unconfined"
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.617648:ERROR:object_proxy.cc(574)] Failed to call method: org.kde.KWallet.isEnabled: object_path= /modules/kwalletd5: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.100" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.kde.KWallet" member="isEnabled" error name="(unset)" requested_reply="0" destination="org.kde.kwalletd5" (uid=1000 pid=2844 comm="/usr/bin/kwalletd5 ")
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.617699:ERROR:kwallet_dbus.cc(100)] Error contacting kwalletd5 (isEnabled)
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.618731:ERROR:object_proxy.cc(574)] Failed to call method: org.kde.KLauncher.start_service_by_desktop_name: object_path= /KLauncher: org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.klauncher was not provided by any .service files
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.618769:ERROR:kwallet_dbus.cc(72)] Error contacting klauncher to start kwalletd5
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.619174:ERROR:object_proxy.cc(574)] Failed to call method: org.kde.KWallet.close: object_path= /modules/kwalletd5: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.100" (uid=1000 pid=2691 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi") interface="org.kde.KWallet" member="close" error name="(unset)" requested_reply="0" destination="org.kde.kwalletd5" (uid=1000 pid=2844 comm="/usr/bin/kwalletd5 ")
Dec  5 23:11:01 myname-PORTEGE-R835 dbus[1703]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/modules/kwalletd5" interface="org.kde.KWallet" member="close" mask="send" name="org.kde.kwalletd5" pid=2691 label="snap.chromium.chromium" peer_pid=2844 peer_label="unconfined"
Dec  5 23:11:01 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: [2691:2816:1205/231101.619209:ERROR:kwallet_dbus.cc(414)] Error contacting kwalletd5 (close)
Dec  5 23:11:23 myname-PORTEGE-R835 Dropbox[2194]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:11:23 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: Unable to monitor entire Dropbox folder hierarchy. Please run "echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  5 23:11:34 myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1690]: QXcbConnection: XCB error: 3 (BadWindow), sequence: 62675, resource id: 127926369, major code: 15
```

---

### Post by howefield on 2017-12-05
Whats the version of Kubuntu that you are using ?

```
cat /ect/*-release
```

---

### Post by vasa1 on 2017-12-05
Also post the output of```
ls /usr/share/xsessions
```please.

Kubuntu doesn't use gdm AFAIK.

And comments such as> 
Still fairly new to Linux......I can't believe it crashed on me tonight. I never thought it was possible. I was brainwashed to think it couldn't crash!! I actually think it's been over 2 years since I last saw a crash like this in Windows 7.may cause your thread to be derailed. So it maybe a good idea to keep to the point :)

---

### Post by frappe792 on 2017-12-05
> **howefield said:**
> Whats the version of Kubuntu that you are using ?

```
cat /ect/*-release
```

I did an exact copy past and 

at: '/ect/*-release': No such file or directory

> **vasa1 said:**
> Also post the output of```
ls /usr/share/xsessions
```please.


```
cinnamon2d.desktop  cinnamon.desktop  kodi.desktop  plasma.desktop  ubuntu.desktop  ubuntu-xorg.desktop  xbmc.desktop
```

---

### Post by yancek on 2017-12-05
> cat /ect/*-release

That's a typo, it should be /etc rather than ect.

---

### Post by vasa1 on 2017-12-05
> **frappe792 said:**
> ```
cinnamon2d.desktop  cinnamon.desktop  kodi.desktop  plasma.desktop  ubuntu.desktop  ubuntu-xorg.desktop  xbmc.desktop
```Note that having several desktop environments on the same system can cause problems.

Developers of each desktop environment may not envisage such mix-n-match situations.

---

### Post by mastablasta on 2017-12-05
> **vasa1 said:**
> Note that having several desktop environments on the same system can cause problems.

Developers of each desktop environment may not envisage such mix-n-match situations.

oh yes, that can cause issues since multiple "applets" and such will be installed. 

Kodi is not needed unless you are running the system on TV and need large desktop interface and remote control support. for viewing videos on PC VLC should be more than adequate.

but enough about desktops. Linux like any other OS can crash. the reasons for crash can be different. sometimes they are easy to pinpont other times they are not. older logs form previous session might provide a clue.

if you experience the desktop crash there are a few options before doing the power down via button:
- switching to different virtual console using ctrl+alt+F2 for example
- using the REISUB command (it might need to be enabled on Ubuntu: [https://ubuntuforums.org/showthread.php?t=2220356](https://ubuntuforums.org/showthread.php?t=2220356) more info: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key))

---

### Post by frappe792 on 2017-12-06
> **yancek said:**
> That's a typo, it should be /etc rather than ect.

haha no problems - here we are

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 17.10"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful
```

> **vasa1 said:**
> Note that having several desktop environments on the same system can cause problems.

Developers of each desktop environment may not envisage such mix-n-match situations.

Hi,

Originally I just downloaded Ubuntu 17.10. You may find in other posts I had issues with the standard ubuntu/gnome desktop and somebody suggest they use KDE as it works alot better on external monitors etc. I found this to be true in my case. (KDE on Ubuntu I understand to be Kubuntu, is that correct?)

Not sure where cinammon came from or kodi (I do have kodi as an app, but not sure why it's available to boot into)

What is your recommendation? I am extremely happy with the current KDE environment, I don't really care about the rest. Are they easy to remove?

> **mastablasta said:**
> 
if you experience the desktop crash there are a few options before doing the power down via button:
- switching to different virtual console using ctrl+alt+F2 for example
- using the REISUB command (it might need to be enabled on Ubuntu: [https://ubuntuforums.org/showthread.php?t=2220356](https://ubuntuforums.org/showthread.php?t=2220356) more info: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key))


I just did the CTRL-ALT-F2 to see what you were talking about but nothing happened?

---

### Post by mastablasta on 2017-12-06
> **frappe792 said:**
> 
Not sure where cinammon came from or kodi (I do have kodi as an app, but not sure why it's available to boot into)


Kodi is not just an app. it is basically a desktop. like i wrote, if you don't need it full screen on TV (or that you are running media server, then you don't need it.

> 
What is your recommendation? I am extremely happy with the current KDE environment, I don't really care about the rest. Are they easy to remove?

KDE is still under heavy development at the moment. some bugs are out some are recurring. it still seems to have good multi monitor support. so if you need that then stay on it.

you can also investigate Neon distribution (stable OS / upgraded KDE).

They are not as easy to remove as they are to add. lets say they create dependencies and removing them also removes dependencies, which might be needed by another desktop. since linux is modular you could remove all and install only the one you like. i think that could work. though easier might be to install it all fresh. 
> 
I just did the CTRL-ALT-F2 to see what you were talking about but nothing happened?
what about alt+f2? or ctrl+alt+F1?

to exit virtual console it should be ctrl+alt+F7 or pressing alt+right arrow repeatedly (to cycle through the consoles)

---

### Post by frappe792 on 2017-12-07
> **mastablasta said:**
> 

what about alt+f2? or ctrl+alt+F1?

to exit virtual console it should be ctrl+alt+F7 or pressing alt+right arrow repeatedly (to cycle through the consoles)

No response on any of those combinations except for ALT+F2 - which is only a shortcut to plasma search.

---

### Post by mastablasta on 2017-12-07
hmm that's a mess then. it should drop you to terminal unless they did something in latest version that would change this.

---

