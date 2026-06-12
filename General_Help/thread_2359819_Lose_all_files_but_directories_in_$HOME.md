---
title: "Lose all files but directories in $HOME"
date: 2017-04-28
forum: General Help
---

### Post by sticnarf on 2017-04-28
Hello, everyone.

My friend comes up with a weird problem. And as a result, nearly all files in my home directory including another disk mounted in $HOME disappear.

He said that he opened Visual Studio Code and updated the C++ plugin. Then, he wrote a small piece of code and compiled them. 

At this time, the system weren't responding. He couldn't do anything but reboot his computer. After that, nearly all files are missing.

Interestingly, the .bashrc file disappears but a lot of other files started with a dot still exists. By the way, the previous .bash_history is also lost, so I don't know about the commands run before.

I find another weird thing. At times, some <script> tags pointing to xg4ken.com are added to web pages. I think it is a hijack but there is little information that I can find on the internet.

Below are the syslog after the system startup (At this time, everything seems ok):
('&#26435;&#38480;&#19981;&#22815;' means 'Permission denied'; '&#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;' means 'No such file or directory')
```

Apr 28 17:53:02 voidlancer-X555LJ avahi-daemon[816]: Registering new address record for fc00:100:100:1::cdf on wlp3s0.*.
Apr 28 17:53:11 voidlancer-X555LJ systemd[1]: Starting Stop ureadahead data collection...
Apr 28 17:53:11 voidlancer-X555LJ systemd[1]: Stopped Read required files in advance.
Apr 28 17:53:11 voidlancer-X555LJ systemd[1]: Started Stop ureadahead data collection.
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/10 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1812/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/10 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1812/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/10 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1772/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:53:38 voidlancer-X555LJ gnome-session[1598]: &#26080;&#27861;&#33719;&#21462; /proc/1812/fd/1023 &#30340;&#25991;&#20214;&#29366;&#24577;: &#26435;&#38480;&#19981;&#22815;
Apr 28 17:54:27 voidlancer-X555LJ systemd[1]: Stopping User Manager for UID 108...
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Stopped target Default.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Reached target Shutdown.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Starting Exit the Session...
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Stopped target Basic System.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Stopped target Sockets.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Stopped target Timers.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Stopped target Paths.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1010]: Received SIGRTMIN+24 from PID 2671 (kill).
Apr 28 17:54:27 voidlancer-X555LJ systemd[1]: Stopped User Manager for UID 108.
Apr 28 17:54:27 voidlancer-X555LJ systemd[1]: Removed slice User Slice of lightdm.
Apr 28 17:54:32 voidlancer-X555LJ wpa_supplicant[980]: wlp3s0: WPA: Group rekeying completed with 44:94:fc:63:30:0f [GTK=CCMP]
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (4 vs 8)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (3 vs 6)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (18 vs 36)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (14 vs 28)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (2 vs 4)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (14 vs 28)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (2 vs 4)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (3 vs 6)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (14 vs 28)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (2 vs 4)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (14 vs 28)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (2 vs 4)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (3 vs 6)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (3 vs 6)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Home[1443]: (unity-scope-home:2690): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Apr 28 17:54:40 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (4 vs 8)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (3 vs 6)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (7 vs 14)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (18 vs 36)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (14 vs 28)
Apr 28 17:54:41 voidlancer-X555LJ com.canonical.Unity.Scope.Applications[1443]: (unity-scope-loader:2701): libunity-protocol-private-WARNING **: protocol-scope-discovery.vala:543: Number of elements of OptionIDs doesn't match OptionNames (2 vs 4)
Apr 28 17:54:50 voidlancer-X555LJ kernel: [  149.702010] show_signal_msg: 39 callbacks suppressed
Apr 28 17:54:50 voidlancer-X555LJ kernel: [  149.702015] Microsoft.VSCod[2909]: segfault at 38 ip 00000000005a5c79 sp 00007f8a927f3580 error 4 in Microsoft.VSCode.CPP.Extension.linux[400000+882000]
Apr 28 17:56:56 voidlancer-X555LJ dbus[764]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Apr 28 17:56:56 voidlancer-X555LJ systemd[1]: Starting Hostname Service...
Apr 28 17:56:56 voidlancer-X555LJ dbus[764]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 28 17:56:56 voidlancer-X555LJ systemd[1]: Started Hostname Service.
Apr 28 17:56:56 voidlancer-X555LJ gnome-session[1598]: Nautilus-Share-Message: Called "net usershare info" but it failed: &#25191;&#34892;&#23376;&#36827;&#31243;“net”&#22833;&#36133;(&#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;)
Apr 28 17:56:56 voidlancer-X555LJ org.gtk.vfs.Daemon[1443]: ** (process:3188): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: &#21518;&#31471;&#19981;&#25903;&#25345;&#30340;&#25805;&#20316;
Apr 28 17:57:37 voidlancer-X555LJ org.gtk.vfs.Daemon[1443]: ** (process:3182): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: &#21518;&#31471;&#19981;&#25903;&#25345;&#30340;&#25805;&#20316;
Apr 28 17:57:39 voidlancer-X555LJ kernel: [  318.847341] perf: interrupt took too long (2535 > 2500), lowering kernel.perf_event_max_sample_rate to 78750
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: qrc:/qml/main.qml:11:5: QML BorderImage: Cannot open: qrc:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/skin2.png
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: qrc:/qml/main.qml:11:5: QML BorderImage: Cannot open: qrc:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/skin2.png
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: inputBackImg width: 61
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: inputBackImg height: 64
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: mainSkin.marginLeft : 2
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: mainSkin.marginRight : 40
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: mainSkin.marginTop : 34
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: mainSkin.marginBottom : 4
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: qrc:/qml/statusBar.qml:263:9: QML Image: Failed to get image from provider: image://status/fan_jian0
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: statusBarPic size: 142 29
Apr 28 17:58:43 voidlancer-X555LJ gnome-session[1598]: qrc:/qml/statusBar.qml:263:9: QML Image: Failed to get image from provider: image://status/fan_jian1
Apr 28 17:59:07 voidlancer-X555LJ kernel: [  406.092120] perf: interrupt took too long (3217 > 3168), lowering kernel.perf_event_max_sample_rate to 62000
Apr 28 18:01:13 voidlancer-X555LJ kernel: [  532.647579] perf: interrupt took too long (4026 > 4021), lowering kernel.perf_event_max_sample_rate to 49500
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/home/voidlancer/doudizhu): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/home/voidlancer/doudizhu' cannot be watched: -2
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/home/voidlancer/.CLion2017.1/system/extResources): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/home/voidlancer/.CLion2017.1/system/extResources' cannot be watched: -2
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed' cannot be watched: -2
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/usr/lib/gcc/x86_64-linux-gnu/5/include): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/usr/lib/gcc/x86_64-linux-gnu/5/include' cannot be watched: -2
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/usr/include): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/usr/include' cannot be watched: -2
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: inotify_add_watch(/usr/local/include): No space left on device
Apr 28 18:01:21 voidlancer-X555LJ fsnotifier[3747]: watch root '/usr/local/include' cannot be watched: -2
Apr 28 18:02:41 voidlancer-X555LJ com.canonical.Unity.Scope.LocalFiles[1443]: (unity-files-daemon:2703): unity-files-daemon-WARNING **: folder.vala:65: Failed to read favorites: &#25171;&#24320;&#25991;&#20214;“/home/voidlancer/.config/gtk-3.0/bookmarks”&#22833;&#36133;&#65306;&#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:04:32 voidlancer-X555LJ wpa_supplicant[980]: wlp3s0: WPA: Group rekeying completed with 44:94:fc:63:30:0f [GTK=CCMP]
Apr 28 18:04:49 voidlancer-X555LJ kernel: [  748.782013] usb 1-1: USB disconnect, device number 2
Apr 28 18:04:49 voidlancer-X555LJ kernel: [  748.782015] usb 1-1.1: USB disconnect, device number 4
Apr 28 18:04:49 voidlancer-X555LJ kernel: [  748.829612] usb 1-1.3: USB disconnect, device number 6
Apr 28 18:04:50 voidlancer-X555LJ kernel: [  748.865539] usb 2-1: USB disconnect, device number 2
Apr 28 18:04:50 voidlancer-X555LJ acpid: input device has been disconnected, fd 13
Apr 28 18:04:50 voidlancer-X555LJ acpid: input device has been disconnected, fd 14
Apr 28 18:04:52 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373892.0508] device (enp2s0): link disconnected (deferring action for 4 seconds)
Apr 28 18:04:52 voidlancer-X555LJ kernel: [  750.913832] r8169 0000:02:00.0 enp2s0: link down
Apr 28 18:04:53 voidlancer-X555LJ kernel: [  752.714496] proc_thermal 0000:00:04.0: Unsupported event [0x84]
Apr 28 18:04:56 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373896.1298] device (enp2s0): link disconnected (calling deferred action)
Apr 28 18:04:56 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373896.1299] device (enp2s0): state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 28 18:04:56 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373896.1345] policy: set 'Sharon' (wlp3s0) as default for IPv4 routing and DNS
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Withdrawing address record for 110.64.87.213 on enp2s0.
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Leaving mDNS multicast group on interface enp2s0.IPv4 with address 110.64.87.213.
Apr 28 18:04:56 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373896.1359] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Interface enp2s0.IPv4 no longer relevant for mDNS.
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Withdrawing address record for 2001:250:3000:3ca2:9b51:52d8:ae40:9734 on enp2s0.
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Leaving mDNS multicast group on interface enp2s0.IPv6 with address 2001:250:3000:3ca2:9b51:52d8:ae40:9734.
Apr 28 18:04:56 voidlancer-X555LJ avahi-daemon[816]: Interface enp2s0.IPv6 no longer relevant for mDNS.
Apr 28 18:04:56 voidlancer-X555LJ dnsmasq[1156]: setting upstream servers from DBus
Apr 28 18:04:56 voidlancer-X555LJ dnsmasq[1156]: using nameserver 192.168.1.1#53(via wlp3s0)
Apr 28 18:04:56 voidlancer-X555LJ dnsmasq[1156]: using nameserver fc00:100:100:1::1#53(via wlp3s0)
Apr 28 18:04:56 voidlancer-X555LJ NetworkManager[810]: <info>  [1493373896.1443] policy: set 'Sharon' (wlp3s0) as default for IPv6 routing and DNS
Apr 28 18:04:56 voidlancer-X555LJ dbus[764]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Apr 28 18:04:56 voidlancer-X555LJ systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr 28 18:04:56 voidlancer-X555LJ dbus[764]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 28 18:04:56 voidlancer-X555LJ systemd[1]: Started Network Manager Script Dispatcher Service.
Apr 28 18:04:56 voidlancer-X555LJ nm-dispatcher: req:1 'down' [enp2s0]: new request (1 scripts)
Apr 28 18:04:56 voidlancer-X555LJ nm-dispatcher: req:1 'down' [enp2s0]: start running ordered scripts...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Bluetooth service...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Session c2 of user voidlancer.
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping ACPI event daemon...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Save/Restore Sound Card State...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopped target Sound Card.
Apr 28 18:05:46 voidlancer-X555LJ bluetoothd[802]: Terminating
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Manage, Install and Generate Color Profiles...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Disk Manager...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopped target Graphical Interface.
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopping Accounts Service...
Apr 28 18:05:46 voidlancer-X555LJ systemd[1]: Stopped target Multi-User System.
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Thermal Daemon Service...
Apr 28 18:05:47 voidlancer-X555LJ thermald[830]: Terminating ...
Apr 28 18:05:47 voidlancer-X555LJ org.gnome.zeitgeist.Engine[1443]: (zeitgeist-daemon:2214): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed
Apr 28 18:05:47 voidlancer-X555LJ ModemManager[811]: <info>  Caught signal, shutting down...
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Modem Manager...
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Regular background program processing daemon...
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Make remote CUPS printers available locally...
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Snappy daemon...
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopped target Login Prompts.
Apr 28 18:05:47 voidlancer-X555LJ systemd[1]: Stopping Getty on tty1...
Apr 28 18:05:47 voidlancer-X555LJ rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="806" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

After the problem happens, here are some of the syslog at startup time:

```

Apr 28 18:06:14 voidlancer-X555LJ rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="758" x-info="http://www.rsyslog.com"] start
Apr 28 18:06:14 voidlancer-X555LJ rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Apr 28 18:06:14 voidlancer-X555LJ rsyslogd: rsyslogd's groupid changed to 108
Apr 28 18:06:14 voidlancer-X555LJ rsyslogd: rsyslogd's userid changed to 104
Apr 28 18:06:14 voidlancer-X555LJ systemd-modules-load[252]: Inserted module 'lp'
Apr 28 18:06:14 voidlancer-X555LJ systemd-modules-load[252]: Inserted module 'ppdev'
Apr 28 18:06:14 voidlancer-X555LJ systemd-modules-load[252]: Inserted module 'parport_pc'
Apr 28 18:06:14 voidlancer-X555LJ loadkeys[251]: &#27491;&#22312;&#21152;&#36733; /etc/console-setup/cached.kmap.gz
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Set console keymap.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Create Static Device Nodes in /dev.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting udev Kernel Device Manager...
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000] microcode: microcode updated early to revision 0x22, date = 2015-09-11
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000] Linux version 4.8.0-49-generic (buildd@lcy01-26) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #52~16.04.1-Ubuntu SMP Thu Apr 20 10:55:59 UTC 2017 (Ubuntu 4.8.0-49.52~16.04.1-generic 4.8.17)
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-49-generic.efi.signed root=UUID=70cf2202-99bd-4241-9d1c-37861e15c208 ro quiet splash vt.handoff=7
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000] KERNEL supported cpus:
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000]   Intel GenuineIntel
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000]   AMD AuthenticAMD
Apr 28 18:06:14 voidlancer-X555LJ kernel: [    0.000000]   Centaur CentaurHauls
Apr 28 18:06:14 voidlancer-X555LJ rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
Apr 28 18:06:14 voidlancer-X555LJ rsyslogd-2007: action 'action 10' suspended, next retry is Fri Apr 28 18:06:44 2017 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started udev Kernel Device Manager.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting Remount Root and Kernel File Systems...
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Remount Root and Kernel File Systems.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting udev Coldplug all Devices...
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting Flush Journal to Persistent Storage...
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting Load/Save Random Seed...
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Reached target Local File Systems (Pre).
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Load/Save Random Seed.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Flush Journal to Persistent Storage.
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.Xauthority: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/user-dirs.dirs: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.dbus/session-bus/2509fa8d992640b68ea7bcee27f75279-0: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/dbus/2509fa8d992640b68ea7bcee27f75279-0: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-quickphrase.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-imselector.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/session_migration-ubuntu: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.ICEauthority: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/gnome-keyring-ssh.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/wallpaper/0_5_1366_768_46a5c46191d90b18a1299b964d454b5d: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/keyrings/user.keystore: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/im-config.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.presage/lm.db: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-spell.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-clipboard.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/clipboard/history.dat: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-chttrans.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-autoeng.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-cloudpinyin.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-xkb.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/data/layout_override: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-unicode.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-pinyin-enhance.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-keyboard.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started udev Coldplug all Devices.
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/snap.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/animation.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/gnomecompat.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/place.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/scale.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/unitymtgrabhandles.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/session.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/composite.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/switcher.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/copytex.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/compiztoolbox.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting Show Plymouth Boot Screen...
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/vpswitch.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/wall.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/commands.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/staticswitcher.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/decor.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/resize.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/expo.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/mousepoll.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/fade.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/opengl.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/unityshell.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/move.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/imgpng.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/core.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/ezoom.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/workarounds.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/matecompat.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/grid.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/compiz-1/compizconfig/done_upgrades: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-classic-ui.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/pulse/cookie: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/pulse/2509fa8d992640b68ea7bcee27f75279-default-sink: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/pulse/2509fa8d992640b68ea7bcee27f75279-default-source: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/user-dirs.locale: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/zeitgeist-vacuum.stamp: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/nautilus/accels: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/drclientlinux.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/activity.sqlite: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/activity.sqlite-wal: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/activity.sqlite-shm: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/flintlock: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/iamchert: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/position.baseB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/postlist.DB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/postlist.baseA: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/postlist.baseB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/record.DB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/record.baseA: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/record.baseB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/termlist.DB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/termlist.baseA: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/position.DB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/position.baseA: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/zeitgeist/fts.index/termlist.baseB: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.xinputrc: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/JetBrains/Toolbox/bin/jetbrains-toolbox: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/thumbnails/normal/6aab606b966a2c55df292abaad4566ab.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/jetbrains-toolbox.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-png.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-rtf.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-txt.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-url.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-vbs.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-wri.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-xml.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/evolution/tasks/system/tasks.ics: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/JetBrains/Toolbox/.settings.json: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-QQ.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/icons/hicolor/256x256/apps/QQ.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-chm.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-gif.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-hlp.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-htm.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-ini.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-jfif.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-jpe.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-mfp.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-msp.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/wine-extension-pdf.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/recently-used.xbel: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/DrClient/DrClientConfig: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/DrClient/DrClientLinux.rcc: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/DrClient/drcomauthsvr: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/DrClient/drcomauthsvr.drsc: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/DrClient/drcomrulesvr.drsc: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/update-notifier-crash-_var_crash__usr_bin_unity-control-center.1000.crash.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/update-notifier-crash-_var_crash__usr_bin_unity-scope-loader.1000.crash.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/update-notifier-crash-_var_crash__usr_bin_vim.basic.1000.crash.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/compizconfig-1/regex.pb: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/hud.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/update-notifier-crash-_var_crash__usr_bin_zeitgeist-daemon.1000.crash.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/upstart-event-bridge.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/ssh-agent.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/update-notifier-release.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/upstart/window-stack-bridge.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/gstreamer-1.0/registry.x86_64.bin: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/Trolltech.conf: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/conf/fcitx-autoeng-ng.config: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/mimeapps.list: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/keyrings/login.keyring: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/fcitx/profile: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/mimeinfo.cache: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/gtk-3.0/bookmarks: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/nautilus/desktop-metadata: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/mimeapps.list: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/&#26700;&#38754;/201630666608: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/applications/netease-cloud-music.desktop: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.cache/gnome-software/3.20/firmware/firmware.xml.gz.asc: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/gvfs-metadata/home: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/gvfs-metadata/home-fc50c697.log: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.local/share/mime/mime.cache: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/&#19979;&#36733;/clion-2017.1.1/bin/clion.svg: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/scdlist.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/scd/15097.scel: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/scd/15117.scel: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/scd/4.scel: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/scd/14108.scel: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/sogouEnv.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.sogouinput/SogouIme_VersionManagerSharedTable__Lock: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.sogouinput/sgim_hz_bin_FileLocker: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/Fuzzy.dat: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/Correction.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/env.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/ban1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/bar.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/cn1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/cn_biaodian1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/menu1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/oh_pagedown_on1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/ov_pageup_off1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/skin.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/save_skin.ini: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/skin2.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/skin/&#40664;&#35748;&#30382;&#32932;/skinmanager1.png: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/sogou-qimpanel/main.conf: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/useSkin.txt: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/sgim_keymap.bin: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.sogouinput/ExtDict_MemLocker: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.sogouinput/KeyPyMap_MemLocker: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/sgim_ext.bin: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.config/SogouPY/pingback.time: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ ureadahead[255]: ureadahead:/home/voidlancer/.java/.userPrefs/jetbrains/jetprofile/prefs.xml: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Show Plymouth Boot Screen.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Created slice system-systemd\x2dbacklight.slice.
Apr 28 18:06:14 voidlancer-X555LJ systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...

```

So what might cause the data loss? The suspected malware or something else? (I find there was a segfault about VSCode, is it possible to delete all the files?)

---

