---
title: "Version 16.04 Very long boot time"
date: 2016-07-31
forum: General Help
---

### Post by anon_private on 2016-07-31
I recently upgraded to version 16.02

I have a number of observations.

First I see a long lost of detail with OK at the left hand side. Is this normal?

When I type in my password it takes about five minuted for the next screen to appear. This is far too long.

I also have to type my wifi password in at each session.

I suspended a session, and later pressed the button on the Dell tower to re-activate the session, the screen went black and I had to reboot.

I have created four virtual desktops and activate the cube, but it appears not to wok. I also want independent desktops but can see the box.

I'd like Homerun kicker back

Any help appreciated

---

### Post by ajgreeny on 2016-07-31
Can I assume that once you have given the wifi password the system connects fine and then runs well, or is it still running too slow?

Check the /var/log/syslog file to see if it is the network that is causing the delay.  Look for any long time differences that show in the listing at the left hand end of each line; I suspect it will relate to networking or wifi, but let's see what the log says before jumping to any conclusions.

---

### Post by anon_private on 2016-08-01
Here is paste from the log

Once I am in the system runs well, but the delays are very frustrating

If I suspend a session I usually need to reboot


```
Aug  1 06:55:44 andrew-Dell-DM061 org.kde.KScreen[2286]: message repeated 7 times: [ kscreen: Primary output changed from KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" ) to KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" )]
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.5647] policy: auto-activating connection 'PlusnetWireless'
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.6671] device (wlan0): Activation: starting connection 'PlusnetWireless' (733e1465-0e5e-4f40-a4cc-20bc0a7e063f)
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.7051] device (wlan0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.7931] manager: NetworkManager state is now CONNECTING
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.7947] device (wlan0): state change: prepare -> config (reason 'none') [40 50 0]
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.7952] device (wlan0): Activation: (wifi) access point 'PlusnetWireless' has security, but secrets are required.
Aug  1 06:56:44 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031004.7953] device (wlan0): state change: config -> need-auth (reason 'none') [50 60 0]
Aug  1 06:57:09 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031029.9527] device (wlan0): No agents were available for this request.
Aug  1 06:57:09 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031029.9527] device (wlan0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug  1 06:57:09 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031029.9945] manager: NetworkManager state is now DISCONNECTED
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031030.1425] device (wlan0): Activation: failed for connection 'PlusnetWireless'
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.1659] device (wlan0): state change: failed -> disconnected (reason 'none') [120 30 0]
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6460] policy: auto-activating connection 'PlusnetWireless'
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6485] device (wlan0): Activation: starting connection 'PlusnetWireless' (d6b7668a-fedf-4bfb-8cd7-7426b4e62c18)
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6490] device (wlan0): state change: disconnected -> prepare (reason 'none') [30 40 0]                                                                         
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6494] manager: NetworkManager state is now CONNECTING                                                                                                         
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6508] device (wlan0): state change: prepare -> config (reason 'none') [40 50 0]                                                                               
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6514] device (wlan0): Activation: (wifi) access point 'PlusnetWireless' has security, but secrets are required.
Aug  1 06:57:10 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031030.6514] device (wlan0): state change: config -> need-auth (reason 'none') [50 60 0]
Aug  1 06:57:35 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031055.6851] device (wlan0): No agents were available for this request.
Aug  1 06:57:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031055.6852] device (wlan0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug  1 06:57:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031055.6858] manager: NetworkManager state is now DISCONNECTED
Aug  1 06:57:35 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031055.6865] device (wlan0): Activation: failed for connection 'PlusnetWireless'
Aug  1 06:57:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031055.6931] device (wlan0): state change: failed -> disconnected (reason 'none') [120 30 0]
Aug  1 06:58:48 andrew-Dell-DM061 anacron[1915]: Job `cron.daily' terminated (mailing output)
Aug  1 06:58:48 andrew-Dell-DM061 anacron[1915]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Aug  1 06:58:48 andrew-Dell-DM061 anacron[1915]: anacron: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Aug  1 06:58:48 andrew-Dell-DM061 anacron[1915]: Normal exit (1 job run)
Aug  1 07:04:11 andrew-Dell-DM061 org.kde.KScreen[2286]: kscreen: Primary output changed from KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" ) to KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" )
Aug  1 07:04:11 andrew-Dell-DM061 org.kde.KScreen[2286]: message repeated 7 times: [ kscreen: Primary output changed from KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" ) to KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" )]
Aug  1 07:04:24 andrew-Dell-DM061 systemd[1]: Starting Cleanup of Temporary Directories...
Aug  1 07:04:24 andrew-Dell-DM061 systemd-tmpfiles[3017]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Aug  1 07:04:24 andrew-Dell-DM061 systemd[1]: Started Cleanup of Temporary Directories.
Aug  1 07:08:20 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031700.9634] device (wlan0): Activation: starting connection 'PlusnetWireless' (733e1465-0e5e-4f40-a4cc-20bc0a7e063f)
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.1889] audit: op="connection-activate" uuid="733e1465-0e5e-4f40-a4cc-20bc0a7e063f" name="PlusnetWireless" pid=2430 uid=1000 result="success"
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.1894] device (wlan0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.1917] manager: NetworkManager state is now CONNECTING
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.2081] device (wlan0): state change: prepare -> config (reason 'none') [40 50 0]
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.2980] device (wlan0): Activation: (wifi) access point 'PlusnetWireless' has security, but secrets are required.
Aug  1 07:08:21 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031701.2981] device (wlan0): state change: config -> need-auth (reason 'none') [50 60 0]
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.6662] device (wlan0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.6671] device (wlan0): state change: prepare -> config (reason 'none') [40 50 0]
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.6864] device (wlan0): Activation: (wifi) connection 'PlusnetWireless' has security, and secrets exist.  No new secrets needed.
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.7097] Config: added 'ssid' value 'PlusnetWireless'
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.7098] Config: added 'scan_ssid' value '1'
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.7099] Config: added 'key_mgmt' value 'WPA-PSK'
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.7099] Config: added 'psk' value '<omitted>'
Aug  1 07:08:29 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031709.7380] sup-iface[0x8526e18,wlan0]: config: set interface ap_scan to 1
Aug  1 07:08:30 andrew-Dell-DM061 org.kde.kdeconnect[2286]: kdeconnect.core: Broadcasting identity packet
Aug  1 07:08:30 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031710.7239] device (wlan0): supplicant interface state: inactive -> scanning
Aug  1 07:08:31 andrew-Dell-DM061 wpa_supplicant[2075]: wlan0: SME: Trying to authenticate with 00:24:17:b8:19:5f (SSID='PlusnetWireless' freq=2462 MHz)
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.877873] wlan0: authenticate with 00:24:17:b8:19:5f
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.888776] wlan0: send auth to 00:24:17:b8:19:5f (try 1/3)
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.893005] wlan0: authenticated
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.893263] rt61pci 0000:03:02.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.893269] rt61pci 0000:03:02.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.896034] wlan0: associate with 00:24:17:b8:19:5f (try 1/3)
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.898760] wlan0: RX AssocResp from 00:24:17:b8:19:5f (capab=0x411 status=0 aid=1)
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.899125] wlan0: associated
Aug  1 07:08:31 andrew-Dell-DM061 kernel: [ 1155.899932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  1 07:08:31 andrew-Dell-DM061 wpa_supplicant[2075]: wlan0: Trying to associate with 00:24:17:b8:19:5f (SSID='PlusnetWireless' freq=2462 MHz)
Aug  1 07:08:31 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031711.8029] device (wlan0): supplicant interface state: scanning -> authenticating
Aug  1 07:08:31 andrew-Dell-DM061 wpa_supplicant[2075]: wlan0: Associated with 00:24:17:b8:19:5f
Aug  1 07:08:31 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031711.8113] device (wlan0): supplicant interface state: authenticating -> associating
Aug  1 07:08:31 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031711.8182] device (wlan0): supplicant interface state: associating -> 4-way handshake
Aug  1 07:08:32 andrew-Dell-DM061 wpa_supplicant[2075]: wlan0: WPA: Key negotiation completed with 00:24:17:b8:19:5f [PTK=CCMP GTK=TKIP]
Aug  1 07:08:32 andrew-Dell-DM061 wpa_supplicant[2075]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:24:17:b8:19:5f completed [id=0 id_str=]
Aug  1 07:08:32 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031712.7945] device (wlan0): supplicant interface state: 4-way handshake -> completed
Aug  1 07:08:32 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031712.7946] device (wlan0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PlusnetWireless'.
Aug  1 07:08:32 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031712.7947] device (wlan0): state change: config -> ip-config (reason 'none') [50 70 0]
Aug  1 07:08:33 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031713.1128] dhcp4 (wlan0): activation: beginning transaction (timeout in 45 seconds)
Aug  1 07:08:33 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031713.4494] dhcp4 (wlan0): dhclient started with pid 3047
Aug  1 07:08:33 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031713.5052] device (wlan0): The kernel does not support extended IFA_FLAGS needed by NM for IPv6 private addresses. This feature is not available
Aug  1 07:08:34 andrew-Dell-DM061 dhclient[3047]: DHCPREQUEST of 192.168.1.64 on wlan0 to 255.255.255.255 port 67 (xid=0x2c8d1622)
Aug  1 07:08:34 andrew-Dell-DM061 dhclient[3047]: DHCPACK of 192.168.1.64 from 192.168.1.254
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1528]   address 192.168.1.64
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1534]   plen 24 (255.255.255.0)
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1540]   gateway 192.168.1.254
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1540]   server identifier 192.168.1.254
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1540]   lease time 86400
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1541]   nameserver '192.168.1.254'
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1541]   domain name 'lan'
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.1542] dhcp4 (wlan0): state changed unknown -> bound
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.2297] device (wlan0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.3080] device (wlan0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.3100] device (wlan0): state change: secondaries -> activated (reason 'none') [90 100 0]
Aug  1 07:08:34 andrew-Dell-DM061 dhclient[3047]: bound to 192.168.1.64 -- renewal in 34442 seconds.
Aug  1 07:08:34 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031714.3104] manager: NetworkManager state is now CONNECTED_LOCAL
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.64.
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: New relevant interface wlan0.IPv4 for mDNS.
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: Registering new address record for 192.168.1.64 on wlan0.IPv4.
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:1fff:fe51:1a74.
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: New relevant interface wlan0.IPv6 for mDNS.
Aug  1 07:08:34 andrew-Dell-DM061 avahi-daemon[1909]: Registering new address record for fe80::21f:1fff:fe51:1a74 on wlan0.*.
Aug  1 07:08:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031715.1372] manager: NetworkManager state is now CONNECTED_GLOBAL
Aug  1 07:08:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031715.1391] policy: set 'PlusnetWireless' (wlan0) as default for IPv4 routing and DNS
Aug  1 07:08:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031715.5724] DNS: starting dnsmasq...
Aug  1 07:08:35 andrew-Dell-DM061 NetworkManager[1917]: <warn>  [1470031715.7502] dnsmasq[0x85167d0]: dnsmasq not found on the bus. The nameserver update will be sent when dnsmasq appears
Aug  1 07:08:35 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031715.9785] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  1 07:08:36 andrew-Dell-DM061 dnsmasq[3057]: started, version 2.75 cache disabled
Aug  1 07:08:36 andrew-Dell-DM061 dnsmasq[3057]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  1 07:08:36 andrew-Dell-DM061 dnsmasq[3057]: DBus support enabled: connected to system bus
Aug  1 07:08:36 andrew-Dell-DM061 dnsmasq[3057]: warning: no upstream servers configured
Aug  1 07:08:37 andrew-Dell-DM061 whoopsie[1758]: [07:08:37] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Aug  1 07:08:38 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031718.5751] device (wlan0): Activation: successful, device activated.
Aug  1 07:08:38 andrew-Dell-DM061 dbus[1768]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Aug  1 07:08:38 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031718.6494] dnsmasq[0x85167d0]: dnsmasq appeared as :1.80
Aug  1 07:08:38 andrew-Dell-DM061 dnsmasq[3057]: setting upstream servers from DBus
Aug  1 07:08:38 andrew-Dell-DM061 dnsmasq[3057]: using nameserver 192.168.1.254#53
Aug  1 07:08:38 andrew-Dell-DM061 NetworkManager[1917]: <info>  [1470031718.6516] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  1 07:08:38 andrew-Dell-DM061 whoopsie[1758]: [07:08:38] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/4
Aug  1 07:08:38 andrew-Dell-DM061 whoopsie[1758]: [07:08:38] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/4
Aug  1 07:08:38 andrew-Dell-DM061 whoopsie[1758]: [07:08:38] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/4
Aug  1 07:08:38 andrew-Dell-DM061 whoopsie[1758]: [07:08:38] online
Aug  1 07:08:39 andrew-Dell-DM061 kernel: [ 1163.408049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:08:39 andrew-Dell-DM061 kernel: [ 1163.860052] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:08:39 andrew-Dell-DM061 systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug  1 07:08:40 andrew-Dell-DM061 dbus[1768]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  1 07:08:40 andrew-Dell-DM061 systemd[1]: Started Network Manager Script Dispatcher Service.
Aug  1 07:08:40 andrew-Dell-DM061 nm-dispatcher: req:1 'up' [wlan0]: new request (1 scripts)
Aug  1 07:08:40 andrew-Dell-DM061 nm-dispatcher: req:1 'up' [wlan0]: start running ordered scripts...
Aug  1 07:08:41 andrew-Dell-DM061 kernel: [ 1165.384018] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:08:41 andrew-Dell-DM061 kernel: [ 1165.884024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:08:42 andrew-Dell-DM061 kernel: [ 1166.384045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:08:42 andrew-Dell-DM061 org.kde.kdeconnect[2286]: kdeconnect.core: Broadcasting identity packet
Aug  1 07:08:56 andrew-Dell-DM061 ntpdate[3187]: step time server 91.189.89.199 offset 0.727255 sec
Aug  1 07:08:56 andrew-Dell-DM061 systemd[2213]: Time has been changed
Aug  1 07:08:56 andrew-Dell-DM061 systemd[1]: Time has been changed
Aug  1 07:08:56 andrew-Dell-DM061 systemd[1]: snapd.refresh.timer: Adding 2h 7min 1.259096s random time.
Aug  1 07:08:56 andrew-Dell-DM061 systemd[1]: apt-daily.timer: Adding 7h 53min 18.450345s random time.
Aug  1 07:08:57 andrew-Dell-DM061 systemd-timesyncd[1155]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
Aug  1 07:10:28 andrew-Dell-DM061 kernel: [ 1271.396030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:28 andrew-Dell-DM061 kernel: [ 1271.556059] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:28 andrew-Dell-DM061 kernel: [ 1271.716102] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:28 andrew-Dell-DM061 kernel: [ 1272.148026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:28 andrew-Dell-DM061 kernel: [ 1272.308044] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:29 andrew-Dell-DM061 kernel: [ 1272.468043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:29 andrew-Dell-DM061 kernel: [ 1272.628035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:29 andrew-Dell-DM061 kernel: [ 1273.060040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:29 andrew-Dell-DM061 kernel: [ 1273.220030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:30 andrew-Dell-DM061 kernel: [ 1273.380045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:30 andrew-Dell-DM061 kernel: [ 1273.540033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:30 andrew-Dell-DM061 kernel: [ 1273.972044] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:30 andrew-Dell-DM061 kernel: [ 1274.132047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:30 andrew-Dell-DM061 kernel: [ 1274.292039] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:31 andrew-Dell-DM061 kernel: [ 1274.452043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:31 andrew-Dell-DM061 kernel: [ 1274.884034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:31 andrew-Dell-DM061 kernel: [ 1275.044046] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:31 andrew-Dell-DM061 kernel: [ 1275.204038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:32 andrew-Dell-DM061 kernel: [ 1275.364044] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:32 andrew-Dell-DM061 kernel: [ 1275.796046] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:32 andrew-Dell-DM061 kernel: [ 1275.956063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:32 andrew-Dell-DM061 kernel: [ 1276.116042] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:32 andrew-Dell-DM061 kernel: [ 1276.276060] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:33 andrew-Dell-DM061 kernel: [ 1276.708046] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:33 andrew-Dell-DM061 kernel: [ 1276.868055] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:33 andrew-Dell-DM061 kernel: [ 1277.028037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:33 andrew-Dell-DM061 kernel: [ 1277.192049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:34 andrew-Dell-DM061 kernel: [ 1277.624034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:34 andrew-Dell-DM061 kernel: [ 1277.784054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:34 andrew-Dell-DM061 kernel: [ 1277.944025] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:34 andrew-Dell-DM061 kernel: [ 1278.104029] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:35 andrew-Dell-DM061 kernel: [ 1278.536045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:35 andrew-Dell-DM061 kernel: [ 1278.696042] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:35 andrew-Dell-DM061 kernel: [ 1278.856034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:35 andrew-Dell-DM061 kernel: [ 1279.016044] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:36 andrew-Dell-DM061 kernel: [ 1279.448049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:36 andrew-Dell-DM061 kernel: [ 1279.608036] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:36 andrew-Dell-DM061 kernel: [ 1279.768033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:36 andrew-Dell-DM061 kernel: [ 1279.928033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:37 andrew-Dell-DM061 kernel: [ 1280.360027] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:37 andrew-Dell-DM061 kernel: [ 1280.520030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:37 andrew-Dell-DM061 kernel: [ 1280.680045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:37 andrew-Dell-DM061 kernel: [ 1280.840040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:37 andrew-Dell-DM061 kernel: [ 1281.272033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:38 andrew-Dell-DM061 kernel: [ 1281.432047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:38 andrew-Dell-DM061 kernel: [ 1281.592038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:38 andrew-Dell-DM061 kernel: [ 1281.752024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:38 andrew-Dell-DM061 kernel: [ 1282.236051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:39 andrew-Dell-DM061 kernel: [ 1282.396023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:39 andrew-Dell-DM061 kernel: [ 1282.556023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:39 andrew-Dell-DM061 kernel: [ 1282.716023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:39 andrew-Dell-DM061 kernel: [ 1283.200026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:40 andrew-Dell-DM061 kernel: [ 1283.360020] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:40 andrew-Dell-DM061 kernel: [ 1283.520047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:10:40 andrew-Dell-DM061 kernel: [ 1283.680030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:10:45 andrew-Dell-DM061 kernel: [ 1288.968026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Aug  1 07:11:50 andrew-Dell-DM061 kernel: [ 1353.936030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:51 andrew-Dell-DM061 kernel: [ 1354.384035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:51 andrew-Dell-DM061 kernel: [ 1354.832034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:51 andrew-Dell-DM061 kernel: [ 1355.280071] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:52 andrew-Dell-DM061 kernel: [ 1355.728025] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:52 andrew-Dell-DM061 kernel: [ 1356.176040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:53 andrew-Dell-DM061 kernel: [ 1356.624029] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:53 andrew-Dell-DM061 kernel: [ 1357.072031] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:54 andrew-Dell-DM061 kernel: [ 1357.520056] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:54 andrew-Dell-DM061 kernel: [ 1357.968026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:55 andrew-Dell-DM061 kernel: [ 1358.416033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:55 andrew-Dell-DM061 kernel: [ 1358.916033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:11:56 andrew-Dell-DM061 kernel: [ 1359.416035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:12:03 andrew-Dell-DM061 org.kde.KScreen[2286]: kscreen: Primary output changed from KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" ) to KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" )
Aug  1 07:13:33 andrew-Dell-DM061 kernel: [ 1457.176026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:34 andrew-Dell-DM061 kernel: [ 1457.624041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:34 andrew-Dell-DM061 kernel: [ 1458.136037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:35 andrew-Dell-DM061 kernel: [ 1458.584037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:35 andrew-Dell-DM061 kernel: [ 1459.032028] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:36 andrew-Dell-DM061 kernel: [ 1459.532029] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:13:36 andrew-Dell-DM061 kernel: [ 1460.032029] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:15:33 andrew-Dell-DM061 kernel: [ 1577.120032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:15:34 andrew-Dell-DM061 kernel: [ 1578.308046] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:15:35 andrew-Dell-DM061 kernel: [ 1579.136048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Aug  1 07:12:09 andrew-Dell-DM061 org.kde.KScreen[2286]: message repeated 7 times: [ kscreen: Primary output changed from KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" ) to KScreen::Output(Id: 574 , Name: "DVI-I-1" ) ( "DVI-I-1" )]
Aug  1 07:17:02 andrew-Dell-DM061 CRON[3371]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
andrew@andrew-Dell-DM061:/var/log$
```

What do I need to update, suspend, or adjust so that I do not have wait so long to login after giving my password?

I used to be able to print, but at present, I note the message ' Filter Failed'. Do I need to update CUPS. When installing 16.04, I did not update CUPS. If necessary, how should I go about the update?

Thanks

I tried to eradiate the problems by renaming some dot files in my home  directory. However, this has made matters worse. I now cannot get 16.04  to boot. I am accessing this page using an old pendrive with Ubuntu  version 12 installed. I also have kubuntu ver 12 on a CD.

I may have to install one of these old versions and lose the data in my home directory. I only have one computer at my dosposal.

Can anyone suggest how I mighr boot 16.04 and repair the files that are causing the problems.

I can get to a spash screen but this is a graphic that I created, put in my password, and that's about as far as I can get.

---

### Post by QDR06VV9 on 2016-08-01
> I may have to install one of these old versions and lose the data in my home directory. I only have one computer at my dosposal.

Just wanted you to know you do not have to lose your data---using the live installer and invoking the file manager as root (sudo nautilus or sudo dolphin or sudo caja) you can move what you need to another storage container IE: USB thumb drive or another source of media storage. See this: [http://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/)
Sorry to hear about the other delima though.:(

---

### Post by QIII on 2016-08-01
Renaming those files was probably one of the most damaging things you might have done.  The operation of the OS under your user is dependent on those files and depends also on their permissions.

Before we go further, do you think you could identify the changed filenames?

---

### Post by anon_private on 2016-08-02
The files I renamed were .kde, .cache, .local, and .config. I was trying to speed up the boot process. I have a  peronalised login screen from a previous version of kubuntu that remained. I could not identify this image in version version 16. How can I eliminate this possible problem?

If I hold down the shift key on booting to the hard drive, I can activate the ubuntu rescue system. I note that there is a root command prompt there. Could I use this feature to re-install using the command do-release-upgrade or something similar.

However, I don't think I will be able to login, unless this sytem allows a login.

What do you think about installing version ca. 12 (either ubuntu or kubuntu) from a pendrive or disk. I prefer the latter (kubuntu on a pendrive).

While I am uisng version 12 fom a pendrive is it safe to do online banking and purchaes online with this dated OS and browser?

Thanks

---

### Post by ajgreeny on 2016-08-02
You could try using a live system to rename those hidden folders; I assume they are still on disk, back to their previous names, after removing the ones that were probably created by the system to replace your renamed versions.

That does not solve your slow login problem but the action you took was not a possible answer for that either.

As for using a 12.# version for online banking, only you can find out if it is possible for you to do it; some banks may not accept the old browsers and security packages that are present in the 12.# live systems.

---

### Post by anon_private on 2016-08-02
I deleted the files. As I recall, I had some difficulty with some of the folders being re-created instantly.

I was wondering if I deletd the dot files that are currently present then that would force the system to re-create these folders.

Regardin version 12 and banking and shopping. I was wondering if financial transaction will be safe

I have managed to located the deleted files in trash (home/andrew/.local/share/trash) using the pendrive; however, I cannot copy them because I do not have the correct permission. I can't locat these files using the command prompt in the live pendrive.In the command prompt I see ubuntu, but in the folder I see andrew

How can I copy them and relocate them to their original positions

Would the utility in ubuntu, obtained through booting and holding shift key, used to obtain the rescue utilities be helpful?

---

### Post by ajgreeny on 2016-08-02
Normally you can only restore files from trash by right-clicking them and choosing Restore; you can not copy files in trash, even as root, and restore them that way so I am not sure if it can be4 done in any way from a live system if you can not login at all.

Just in case it helps you, here is some info about managing trash from the command-line.

---

### Post by anon_private on 2016-08-02
I tried installing boot repair using 

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

Ubfortuanately, the package was not located.

Do you think that it might be a good idea to delete those dot files, reboot, and hope that the system re-creates the dot files that will allow a boot?

---

### Post by QIII on 2016-08-02
Hello!

Your initial slow boot process was more than likely caused by systemd's reaction to improperly configured ethernet and wifi.  If you don't have a wired connection but have not removed your ethernet from the config file, you can sometimes get a 90 second halt while systemd waits to see if the connection comes up, followed by an additional 30 second wait.

The same may happen with wifi.  Together, that's a possible delay of 4 minutes just due to connectivity issues.

By renaming files that may be critical to booting and arriving at your account login, you went from a slow boot to no boot.  Then, as I read it, you deleted some files or directories hoping that they would be regenerated.  Did you do that a second time?

I don't understand what leads you to believe that all critical files will automagically be regenerated if you delete things.

I am going to be brutally honest:  had you simply renamed the changed files back to their original names, there might have been a chance that the permissions were unchanged.  In that case, you would have been back to a slow booting -- but still booting -- OS.  Now, your machine is in an unknown state with files/directoriess that may be randomly missing.  It seems now that you are throwing stuff against the wall to see what sticks.  That rarely works and usually leads to a mess.

I think you may be at one of two situations where I recommend a reinstallation:  a compromised machine or a filesystem that has been randomly modified.

---

### Post by anon_private on 2016-08-03
Regarding installation.

I have tried to burn folders from my home directory using Brasero on the live pendrive.

Things seemed to be goung well, but I received an error. I must have made a mistake since the DVD +R appears to be full (it should not be). It is a RW disk, so I should be able to delete the files and start again.

I cannot see the DVD on the desktop, or in the Home folder icon. Brasero, my version at least, has no delete options.

Question 1:  How can I delete the files on the DVD +R and start again?

Next. I will need to download the kununtu 16.04 iso file. If space allows can I put it on the same disk as my burned files?

It has been so long since I have done this. Once I have the iso file, how do I install it?

Thanks

Ps. File system: /media/cdrom appears to be my live pendrive
hard drive: /media/andrew (will not open: permission problem)

---

### Post by ajgreeny on 2016-08-03
You can't delete files from a DVD-RW; you can only start again and burn the disk afresh.  A DVD-RW has a totally different filesystem to a normal hard disk and it is impossible (in Linux at least, no idea about Windows) to delete files from it and replace with others without a complete burn process.

However, I do not understand what you are attempting to do by burning the folders from your desktop; is that a different machine from the one with the problem?

---

### Post by anon_private on 2016-08-03
I would like to burn the files in my home directory because it looks like I will need to re-install my operating system.

According to the version of Brasero that is part of the live pendrive my DVD+R has little space and will not allow a burn

Hope I can get to grips with using iso files and the problem of burning with Brassero

---

### Post by anon_private on 2016-08-04
> **QIII said:**
> Hello!

Your initial slow boot process was more than likely caused by systemd's reaction to improperly configured ethernet and wifi.  If you don't have a wired connection but have not removed your ethernet from the config file, you can sometimes get a 90 second halt while systemd waits to see if the connection comes up, followed by an additional 30 second wait.

The same may happen with wifi.  Together, that's a possible delay of 4 minutes just due to connectivity issues.

By renaming files that may be critical to booting and arriving at your account login, you went from a slow boot to no boot.  Then, as I read it, you deleted some files or directories hoping that they would be regenerated.  Did you do that a second time?

I don't understand what leads you to believe that all critical files will automagically be regenerated if you delete things.

I am going to be brutally honest:  had you simply renamed the changed files back to their original names, there might have been a chance that the permissions were unchanged.  In that case, you would have been back to a slow booting -- but still booting -- OS.  Now, your machine is in an unknown state with files/directoriess that may be randomly missing.  It seems now that you are throwing stuff against the wall to see what sticks.  That rarely works and usually leads to a mess.

I think you may be at one of two situations where I recommend a reinstallation:  a compromised machine or a filesystem that has been randomly modified.


How can I copy the directories in my home folder using the pendrive OS and Braserro

---

### Post by ajgreeny on 2016-08-04
> **anon_private said:**
> How can I copy the directories in my home folder using the pendrive OS and Braserro
You can't.

Brasero is an application for burning CDs or DVDs; it has nothing to do with copying files and folders to a pendrive which you can do with drag and drop in a file manager, or using the cp command in terminal.

I still do not understand why you want to copy folders that are probably not the originals in the OS to your home in order to reinstall, if that is what you're trying to do.

---

### Post by anon_private on 2016-08-04
It appears that Brasero cannot delete files on a DVD+R disk. Windows shows the DVD empty. Brasero thinks it is almost full.

Regarding copying the files in my corrupted system. I am referring to images, videos, music, downlaods, documents, etc in my home directory.

I note that there is a new version of 16.04 (.1). I assume that this is preferred aver 16.04. I hope that the memory requirements are the same.

---

### Post by ajgreeny on 2016-08-04
> **anon_private said:**
> It appears that Brasero cannot delete files on a DVD+R disk. Windows shows the DVD empty. Brasero thinks it is almost full.Yes it will.
A DVD+R disk can be written to only once and not deleted or blanked in any way.  As I said before you can not even delete files separately from a DVD+RW; you would have to blank the disk completely using something like brasero and then re-write it as it is not a hard disk filesystem.

> Regarding copying the files in my corrupted system. I am referring to images, videos, music, downlaods, documents, etc in my home directory.OK, that is a good reason for doing so as they are just data files and can be copied to the pendrive using nautilus in a live system if necessary.

> I note that there is a new version of 16.04 (.1). I assume that this is preferred aver 16.04. I hope that the memory requirements are the same.I suggest you try 16.04.1 live first as there can be a few problems, mainly with AMD graphics, depending on your hardware. Probably it will run very sweetly and use no more memory than 14.04 so is worth trying.

---

### Post by anon_private on 2016-08-04
Thank you.

If I understand you correctly, once a DVD+R is written,, even with a small file, then the DVD cannot be further accessed (written). I wonder if Brasero finalises the disk automatically?

I will investigate Nautilus.

I have downloaded the 16.0.4.1 iso file (32 bit) and have created a live DVD.

Things seem to be working well. So far, the only problem that I have noticed is an almost horizontal white line at the top of the background graphic. However, I only have one GB of RAM. This line might disappear after installation.

Is it possible, as part of the installation process, to activate a box that will ensure that kubuntu does not overwrite the home directory, or must I copy the files/folders?

When installing, is it best to be connected to the Internet in case the disk needs some files, or is this not necessary?

---

### Post by mook765 on 2016-08-06
When installing, it is the very best to be connected to the internet via Lan.
You should think about choosing a different distribution, Lubuntu or Xubuntu.
These distributions have a much lighter desktop environment and will run smoother on your machine which has a bit low specs...

---

### Post by anon_private on 2016-08-06
I have never had a problem running kubuntu on my machine

---

