---
title: "Kubuntu 18.04 freezing repeatedly today after being stable in past"
date: 2018-08-31
forum: General Help
---

### Post by sgian on 2018-08-31
Hello,
I have been running Kubuntu 18.04 for a while (months?) and haven't had any problems.  File Search was disabled immediately after installation.  System is an AMD A8-7650K Quad Core CPU and 8 GB of RAM on a MSI A68H Grenade motherboard.  4.15.0-33 kernel, system updated this morning with apt update/upgrade.  The changes today were updates, and adding a Nettis WF2113 internal wireless adapter.  My other Kubuntu 18.04 installation on an Intel dual core and the same wireless adapter hasn't been freezing up after the updates, as far as I can tell.

The first freeze appears to be Xapian, even though File Search is disabled (I checked). Here is a copy/paste from nano /var/log/syslog
```
Aug 31 10:45:05 Quad-Kubu1804 nm-dispatcher: req:1 'up' [wlp3s0]: new request (1 scripts)
Aug 31 10:45:05 Quad-Kubu1804 nm-dispatcher: req:1 'up' [wlp3s0]: start running ordered scripts...
Aug 31 10:45:05 Quad-Kubu1804 nm-dispatcher: req:2 'connectivity-change': new request (1 scripts)
Aug 31 10:45:05 Quad-Kubu1804 systemd-resolved[898]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
Aug 31 10:45:05 Quad-Kubu1804 nm-dispatcher: req:2 'connectivity-change': start running ordered scripts...
Aug 31 10:45:06 Quad-Kubu1804 avahi-daemon[940]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::641a:5395:d15a:37e2.
Aug 31 10:45:06 Quad-Kubu1804 avahi-daemon[940]: New relevant interface wlp3s0.IPv6 for mDNS.
Aug 31 10:45:06 Quad-Kubu1804 avahi-daemon[940]: Registering new address record for fe80::641a:5395:d15a:37e2 on wlp3s0.*.
Aug 31 10:45:07 Quad-Kubu1804 NetworkManager[943]: <info>  [1535730307.3249] dhcp6 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Aug 31 10:45:07 Quad-Kubu1804 NetworkManager[943]: <info>  [1535730307.3277] dhcp6 (wlp3s0): dhclient started with pid 1971
Aug 31 10:45:07 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 940ms.
Aug 31 10:45:08 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 1820ms.
Aug 31 10:45:10 Quad-Kubu1804 whoopsie[1140]: [10:45:10] online
Aug 31 10:45:10 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 3710ms.
Aug 31 10:45:14 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 7220ms.
Aug 31 10:45:17 Quad-Kubu1804 systemd-timesyncd[897]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Aug 31 10:45:17 Quad-Kubu1804 systemd-timesyncd[897]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Aug 31 10:45:21 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 14710ms.
Aug 31 10:45:36 Quad-Kubu1804 dhclient[1971]: XMT: Info-Request on wlp3s0, interval 28540ms.
Aug 31 10:45:44 Quad-Kubu1804 org.kde.ActivityManager[1388]: Creating the cache for:  "applications:thunderbird.desktop"
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]: Already in database?  true
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:       First update :  QDateTime(2018-04-14 13:29:57.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:        Last update :  QDateTime(2018-08-31 06:48:43.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]: After the adjustment
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:      Current score :  68.1597
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:       First update :  QDateTime(2018-04-14 13:29:57.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:        Last update :  QDateTime(2018-08-31 06:48:43.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]: Interval length is  0
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]:          New score :  69.1597
Aug 31 10:45:45 Quad-Kubu1804 org.kde.ActivityManager[1388]: ResourceScoreUpdated: "efbe44db-806e-4cd2-8a0d-7aa6c6a10ad5" "org.kde.plasma.kicker" "applications:thunderbird.desktop"
Aug 31 10:45:52 Quad-Kubu1804 NetworkManager[943]: <warn>  [1535730352.2306] dhcp6 (wlp3s0): request timed out
Aug 31 10:45:52 Quad-Kubu1804 NetworkManager[943]: <info>  [1535730352.2306] dhcp6 (wlp3s0): state changed unknown -> timeout
Aug 31 10:45:52 Quad-Kubu1804 NetworkManager[943]: <info>  [1535730352.2315] dhcp6 (wlp3s0): canceled DHCP transaction, DHCP client pid 1971
Aug 31 10:45:52 Quad-Kubu1804 NetworkManager[943]: <info>  [1535730352.2315] dhcp6 (wlp3s0): state changed timeout -> done
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]: Creating the cache for:  "applications:firefox.desktop"
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]: Already in database?  true
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:       First update :  QDateTime(2018-04-14 11:16:25.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:        Last update :  QDateTime(2018-08-30 16:44:56.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]: After the adjustment
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:      Current score :  117.101
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:       First update :  QDateTime(2018-04-14 11:16:25.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:        Last update :  QDateTime(2018-08-30 16:44:56.000 CDT Qt::TimeSpec(LocalTime))
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]: Interval length is  0
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]:          New score :  118.101
Aug 31 10:46:32 Quad-Kubu1804 org.kde.ActivityManager[1388]: ResourceScoreUpdated: "efbe44db-806e-4cd2-8a0d-7aa6c6a10ad5" "org.kde.plasma.kicker" "applications:firefox.desktop"
Aug 31 10:47:21 Quad-Kubu1804 dbus-daemon[917]: [system] Activating service name='org.debian.AptXapianIndex' requested by ':1.36' (uid=1000 pid=1443 comm="kded5 [kdeinit5]                                  " label="unconfi$
Aug 31 10:47:21 Quad-Kubu1804 dbus-daemon[917]: [system] Successfully activated service 'org.debian.AptXapianIndex'
Aug 31 10:47:24 Quad-Kubu1804 kernel: [  286.909449] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:d4:6e:0e:8d:8a:ab:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2

```

I couldn't figure out what happened the second time with syslog, the screen had gone black and I couldn't wake the screen back up.  Power settings are not set to hibernate or sleep at all, and this never happened before.
```
Aug 31 12:02:37 Quad-Kubu1804 systemd[1]: Started Run anacron jobs.
Aug 31 12:02:37 Quad-Kubu1804 anacron[5120]: Anacron 2.3 started on 2018-08-31
Aug 31 12:02:37 Quad-Kubu1804 anacron[5120]: Normal exit (0 jobs run)
Aug 31 12:11:26 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Aug 31 12:11:36 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
Aug 31 12:11:46 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Aug 31 12:11:47 Quad-Kubu1804 systemd-timesyncd[905]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
Aug 31 12:17:01 Quad-Kubu1804 CRON[5435]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 12:17:12 Quad-Kubu1804 dbus-daemon[918]: [system] Activating service name='org.kde.powerdevil.backlighthelper' requested by ':1.41' (uid=1000 pid=1619 comm="/usr/lib/x86_64-linux-gnu/libexec/org_kde_powerdev" label$
Aug 31 12:17:12 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: QDBusArgument: read from a write-only object
Aug 31 12:17:12 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: message repeated 2 times: [ QDBusArgument: read from a write-only object]
Aug 31 12:17:12 Quad-Kubu1804 dbus-daemon[918]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Aug 31 12:17:58 Quad-Kubu1804 systemd-resolved[906]: Grace period over, resuming full feature set (UDP+EDNS0) for DNS server 192.168.1.1.
Aug 31 12:18:02 Quad-Kubu1804 systemd-resolved[906]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
Aug 31 12:21:09 Quad-Kubu1804 kernel: [ 5259.866017] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:d4:6e:0e:8d:8a:ab:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Aug 31 12:22:33 Quad-Kubu1804 dbus-daemon[918]: [system] Activating service name='org.kde.powerdevil.backlighthelper' requested by ':1.41' (uid=1000 pid=1619 comm="/usr/lib/x86_64-linux-gnu/libexec/org_kde_powerdev" label$
Aug 31 12:22:33 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: QDBusArgument: read from a write-only object
Aug 31 12:22:33 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: message repeated 2 times: [ QDBusArgument: read from a write-only object]
Aug 31 12:22:33 Quad-Kubu1804 dbus-daemon[918]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Aug 31 12:23:48 Quad-Kubu1804 dbus-daemon[918]: [system] Activating service name='org.kde.powerdevil.backlighthelper' requested by ':1.41' (uid=1000 pid=1619 comm="/usr/lib/x86_64-linux-gnu/libexec/org_kde_powerdev" label$
Aug 31 12:23:48 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: QDBusArgument: read from a write-only object
Aug 31 12:23:48 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: message repeated 2 times: [ QDBusArgument: read from a write-only object]
Aug 31 12:23:48 Quad-Kubu1804 dbus-daemon[918]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Aug 31 12:24:49 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Aug 31 12:25:03 Quad-Kubu1804 dbus-daemon[918]: [system] Activating service name='org.kde.powerdevil.backlighthelper' requested by ':1.41' (uid=1000 pid=1619 comm="/usr/lib/x86_64-linux-gnu/libexec/org_kde_powerdev" label$
Aug 31 12:25:03 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: QDBusArgument: read from a write-only object
Aug 31 12:25:03 Quad-Kubu1804 org.kde.powerdevil.backlighthelper: message repeated 2 times: [ QDBusArgument: read from a write-only object]
Aug 31 12:25:03 Quad-Kubu1804 dbus-daemon[918]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Aug 31 12:26:04 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Aug 31 12:26:14 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
Aug 31 12:26:24 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Aug 31 12:26:34 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Aug 31 12:28:53 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Aug 31 12:29:04 Quad-Kubu1804 systemd-timesyncd[905]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Aug 31 12:29:04 Quad-Kubu1804 systemd-timesyncd[905]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Aug 31 12:29:29 Quad-Kubu1804 kernel: [ 5760.018129] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:d4:6e:0e:8d:8a:ab:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Aug 31 12:31:34 Quad-Kubu1804 kernel: [ 5885.158557] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:d4:6e:0e:8d:8a:ab:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2

```

---

### Post by sgian on 2018-09-01
If anyone else has this problem and comes across this thread, taking the wireless card out fixed the problem.  I only have a 400W power supply for a quad core cpu and graphics card, so I guess I need more power to have the wireless card.

---

