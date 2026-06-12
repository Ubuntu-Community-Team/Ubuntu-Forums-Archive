---
title: "When starting after suspend, Ubuntu is in read-only mode and everything fails"
date: 2021-08-10
forum: General Help
---

### Post by Paddy Landau on 2021-08-10
Suspend on Ubuntu 20.04 used to work perfectly (well, nearly; occasionally it would power down instead of suspending).

However, recently, it has a different habit. When trying to resume from suspend, Ubuntu can't properly awaken, giving me a degraded login screen that doesn't accept input. This happens every time, instead of intermittently.

When it happens, I can use Ctrl+Alt+F1 to go to the console, where I see a ton of messages showing that the disk is read-only. The only way for me to recover is [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses").

During reboot, I can see that the system repairs the disk from problems caused by the shutdown.

As the system was read-only on trying to resume from suspend, naturally there are no error logs for that. However, journalctl reveals a few entries from when the system begins the suspend process. Below, I've included the full set of logs from when the suspend process begins to when the machine was suspended. ("Fiamma" is the name of my computer.)

The entries after that all pertain to the reboot.

I can't spot a problem in these logs. Can you? Or, can you advise me on what to do next?

Thank you

```
-- Logs begin at Sat 2021-05-29 12:55:21 BST, end at Tue 2021-08-10 14:22:45 BST. --
Aug 10 14:11:23 Fiamma kernel: **Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7**
Aug 10 14:11:23 Fiamma kernel: **Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7**
Aug 10 14:11:23 Fiamma kernel: [B]audit: type=1107 audit(1628601083.623:113): pid=1581 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=9802 label="snap.keepassxc.keepassxc" peer_pid=1618 peer_label="unconfined"
                                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'[/B]
Aug 10 14:11:23 Fiamma audit[1581]: [COLOR=#008080]USER_AVC pid=1581 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=9802 label="snap.keepassxc.keepassxc" peer_pid=1618 peer_label="unconfined"
                                     exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'[/COLOR]
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6261] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6264] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6273] manager: NetworkManager state is now ASLEEP
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6277] device (wlo1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Aug 10 14:11:23 Fiamma whoopsie[5286]: [14:11:23] offline
Aug 10 14:11:23 Fiamma dbus-daemon[1581]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=1582 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Aug 10 14:11:23 Fiamma systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 10 14:11:23 Fiamma dbus-daemon[1581]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 10 14:11:23 Fiamma systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 10 14:11:23 Fiamma kernel: wlo1: deauthenticating from e4:57:40:93:30:f6 by local choice (Reason: 3=DEAUTH_LEAVING)
Aug 10 14:11:23 Fiamma wpa_supplicant[1622]: **wlo1: CTRL-EVENT-DISCONNECTED bssid=e4:57:40:93:30:f6 reason=3 locally_generated=1**
Aug 10 14:11:23 Fiamma NetworkManager[1582]: [COLOR=#daa520]<warn>  [1628601083.6489] sup-iface[0x55c9e07e6920,wlo1]: connection disconnected (reason -3)[/COLOR]
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6493] device (wlo1): supplicant interface state: completed -> disconnected
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6495] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Withdrawing address record for fe80::dfd0:8385:a84a:4906 on wlo1.
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Leaving mDNS multicast group on interface wlo1.IPv6 with address fe80::dfd0:8385:a84a:4906.
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Interface wlo1.IPv6 no longer relevant for mDNS.
Aug 10 14:11:23 Fiamma whoopsie[5286]: [14:11:23] Cannot reach: https://daisy.ubuntu.com
Aug 10 14:11:23 Fiamma gnome-shell[6856]: **An active wireless connection, in infrastructure mode, involves no access point?**
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6927] dhcp4 (wlo1): canceled DHCP transaction
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6927] dhcp4 (wlo1): state changed bound -> done
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Withdrawing address record for 192.168.0.28 on wlo1.
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Leaving mDNS multicast group on interface wlo1.IPv4 with address 192.168.0.28.
Aug 10 14:11:23 Fiamma avahi-daemon[1573]: Interface wlo1.IPv4 no longer relevant for mDNS.
Aug 10 14:11:23 Fiamma NetworkManager[1582]: <info>  [1628601083.6953] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Aug 10 14:11:23 Fiamma nm-dispatcher[48960]: run-parts: failed to stat component /etc/network/if-post-down.d/avahi-daemon: No such file or directory
Aug 10 14:11:23 Fiamma wpa_supplicant[1622]: **wlo1: CTRL-EVENT-SCAN-FAILED ret=-100**
Aug 10 14:11:23 Fiamma wpa_supplicant[1622]: **nl80211: deinit ifname=p2p-dev-wlo1 disabled_11b_rates=0**
Aug 10 14:11:23 Fiamma systemd[1]: Reached target Sleep.
Aug 10 14:11:23 Fiamma systemd[1]: Starting Suspend...
Aug 10 14:11:23 Fiamma systemd[1]: Stopping Atop advanced performance monitor...
Aug 10 14:11:23 Fiamma wpa_supplicant[1622]: **nl80211: deinit ifname=wlo1 disabled_11b_rates=0**
Aug 10 14:11:24 Fiamma systemd[1]: atop.service: Succeeded.
Aug 10 14:11:24 Fiamma systemd[1]: Stopped Atop advanced performance monitor.
Aug 10 14:11:24 Fiamma systemd-sleep[48965]: Suspending system...
Aug 10 14:11:24 Fiamma kernel: PM: suspend entry (s2idle)
```

---

### Post by Paddy Landau on 2021-08-13
[Solution found]("https://ubuntuforums.org/showthread.php?t=2465731").

There's a [bug in the latest Linux kernel]("https://ubuntuforums.org/showthread.php?t=2465731&page=2&p=14053502&viewfull=1#post14053502").

---

