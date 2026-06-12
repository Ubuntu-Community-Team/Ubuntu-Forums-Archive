---
title: "System automatically shuts down after upgrade to 20.04 LTS"
date: 2020-05-11
forum: General Help
---

### Post by terence8888 on 2020-05-11
Hi,

I just upgraded from 16.04 to 20.04 (via 18.04).  Everything works apart from the fact that the system shuts down by itself.  I look at /var/log/syslog and see that it shuts down but no clue which process is causing it.  I've set the power management to never sleep and never suspend.  The machine is used as a server so should never poweroff.  Any help will be much appreciated!

An excerpt from the log:

.....
May  9 07:58:50 wotan systemd-timesyncd[822]: Initial synchronization to time server 91.189.91.157:123 (ntp.ubuntu.com).
May  9 08:09:01 wotan CRON[77158]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
May  9 08:09:05 wotan systemd[1]: Starting Clean php session files...
May  9 08:09:05 wotan systemd[1]: phpsessionclean.service: Succeeded.
May  9 08:09:05 wotan systemd[1]: Finished Clean php session files.
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.5788] manager: sleep: sleep requested (sleeping: no  enabled: yes)
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.5789] device (eth0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.5972] manager: NetworkManager state is now ASLEEP
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.5986] device (eth1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
May  9 08:13:45 wotan whoopsie[1246]: [08:13:45] offline
May  9 08:13:45 wotan dbus-daemon[904]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=905 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May  9 08:13:45 wotan systemd[1]: Starting Network Manager Script Dispatcher Service...
May  9 08:13:45 wotan dbus-daemon[904]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  9 08:13:45 wotan systemd[1]: Started Network Manager Script Dispatcher Service.
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.6424] device (eth1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
May  9 08:13:45 wotan avahi-daemon[900]: Withdrawing address record for fe80::76d4:35ff:fe13:9055 on eth1.
May  9 08:13:45 wotan avahi-daemon[900]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::76d4:35ff:fe13:9055.
May  9 08:13:45 wotan avahi-daemon[900]: Interface eth1.IPv6 no longer relevant for mDNS.
May  9 08:13:45 wotan avahi-daemon[900]: Withdrawing address record for 192.168.1.88 on eth1.
May  9 08:13:45 wotan avahi-daemon[900]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.88.
May  9 08:13:45 wotan avahi-daemon[900]: Interface eth1.IPv4 no longer relevant for mDNS.
May  9 08:13:45 wotan NetworkManager[905]: <info>  [1589008425.6950] device (eth1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
May  9 08:13:45 wotan kernel: [332702.925051] r8169 0000:02:00.0 eth1: Link is Down
May  9 08:13:45 wotan systemd[1]: Reached target Sleep.
May  9 08:13:45 wotan systemd[1]: Starting Suspend...
May  9 08:13:45 wotan systemd-sleep[77285]: Suspending system...
May  9 08:13:45 wotan kernel: [332702.992343] PM: suspend entry (deep)

---

