---
title: "Crash - how to read log files"
date: 2014-11-04
forum: General Help
---

### Post by tigerjack89 on 2014-11-04
A few days ago the laptop decided to close without no relevant reason. From this day on, it randomly crashes without explanation.
This is what I (correctly?) filtered from the log files on the last crash, but I don't know what it means. At the time there are several process running: many web pages on chrome and firefox, a virtualbox machine with WindowsXP and the clamscan service.
What the root cause of the problem is? Also, do you think I have to activate the `apport` service in order to get more infos?

****/var/log/kern.log****
```

    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.148059] wlan0: deauthenticating from f8:35:dd:77:3a:04 by local choice (reason=3)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.176190] cfg80211: Calling CRDA to update world regulatory domain
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227383] cfg80211: World regulatory domain updated:
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227386] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227387] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227389] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227390] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227390] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227391] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```
****/var/log/syslog****
```
    Nov  4 10:53:12 tigerjack89-Inspiron-7720 compiz: pam_ecryptfs: seteuid error
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> sleep requested (sleeping: no  enabled: yes)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> sleeping or disabling...
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (wlan0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (wlan0): deactivating device (reason 'sleeping') [37]
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4656
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Withdrawing address record for fe80::6236:ddff:fe41:415f on wlan0.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::6236:ddff:fe41:415f.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Interface wlan0.IPv6 no longer relevant for mDNS.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.148059] wlan0: deauthenticating from f8:35:dd:77:3a:04 by local choice (reason=3)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 wpa_supplicant[1600]: wlan0: CTRL-EVENT-DISCONNECTED bssid=f8:35:dd:77:3a:04 reason=3 locally_generated=1
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Withdrawing address record for 192.168.1.152 on wlan0.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.152.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 avahi-daemon[1102]: Interface wlan0.IPv4 no longer relevant for mDNS.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.176190] cfg80211: Calling CRDA to update world regulatory domain
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <warn> DNS: plugin dnsmasq update failed
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> Removing DNS information from /sbin/resolvconf
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 dnsmasq[2856]: setting upstream servers from DBus
    Nov  4 09:49:27 tigerjack89-Inspiron-7720 whoopsie[1357]: message repeated 2 times: [ online]
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 whoopsie[1357]: offline
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227383] cfg80211: World regulatory domain updated:
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227386] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227387] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227389] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227390] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227390] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 kernel: [ 4191.227391] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (wlan0): cleaning up...
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (wlan0): taking down device.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> NetworkManager state is now ASLEEP
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (eth1): cleaning up...
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 NetworkManager[1121]: <info> (eth1): taking down device.
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 dbus[1058]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 dbus[1058]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 dbus[1058]: [system] Successfully activated service 'org.freedesktop.systemd1'
    Nov  4 10:53:55 tigerjack89-Inspiron-7720 dbus[1058]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
    Nov  4 10:53:56 tigerjack89-Inspiron-7720 anacron[6005]: Anacron 2.3 started on 2014-11-04
    Nov  4 10:53:56 tigerjack89-Inspiron-7720 anacron[6005]: Normal exit (0 jobs run)

```

****EDIT****
While the previous contain all the logs that *I thougth* was relevant to the crash (inspecting the timestamps), these are the links to the full logs


 - [syslog.1]("http://pastebin.com/gygDAeUj")
 - kern.log.1 [part1]("http://pastebin.com/Q0KVEusR") [part2]("http://pastebin.com/XF11dRjW")
 - [dmesg.0]("http://pastebin.com/tEQsbtXe")

---

