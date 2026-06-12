---
title: "wifi spontaniously vanished on ubuntu 20.04"
date: 2022-04-04
forum: General Help
---

### Post by chopra on 2022-04-04
Hi guys,
I just installed ubuntu 20.04 on a new machine, a dynabook tecra A50F

All of a sudden, my internet went completely down.

A short while before it went down, I had turned wifi off and back on, which I do when it starts to slow down.

I have a dual boot, and internet works fine on windows, as well as another ubuntu machine.

As can be seen from the settings attachment, wireless is not even something that the machine acknowledges to exist.

I did paste something from the /var/log/syslog file that occured around the time it occured.

I'm not sure what to make of this.

Thanks, Chopra

Apr  4 21:44:07 dynabook-TECRA-A50-F kernel: [ 6900.219994] wlp1s0: deauthenticating from a0:2d:13:2b:87:e6 by local choice (Reason: 3=DEAUTH_LEAVING)
Apr  4 21:44:07 dynabook-TECRA-A50-F wpa_supplicant[819]: wlp1s0: CTRL-EVENT-DISCONNECTED bssid=a0:2d:13:2b:87:e6 reason=3 locally_generated=1
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Interface wlp1s0.IPv6 no longer relevant for mDNS.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Leaving mDNS multicast group on interface wlp1s0.IPv6 with address 2600:1700:9320:2970:c583:c72d:c720:2cc3.
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0040] manager: rfkill: Wi-Fi hardware radio set disabled
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0042] device (wlp1s0): state change: activated -> unavailable (reason 'none', sys-iface-state: 'managed')
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Interface wlp1s0.IPv4 no longer relevant for mDNS.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Leaving mDNS multicast group on interface wlp1s0.IPv4 with address 192.168.1.70.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Withdrawing address record for 2600:1700:9320:2970::559 on wlp1s0.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Withdrawing address record for 2600:1700:9320:2970:4b33:53ee:b120:b66 on wlp1s0.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Withdrawing address record for 2600:1700:9320:2970:c583:c72d:c720:2cc3 on wlp1s0.
Apr  4 21:44:08 dynabook-TECRA-A50-F avahi-daemon[777]: Withdrawing address record for 192.168.1.70 on wlp1s0.
Apr  4 21:44:08 dynabook-TECRA-A50-F systemd[1]: Starting Load/Save RF Kill Switch Status...
Apr  4 21:44:08 dynabook-TECRA-A50-F whoopsie[1187]: [21:44:08] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Apr  4 21:44:08 dynabook-TECRA-A50-F whoopsie[1187]: [21:44:08] offline
Apr  4 21:44:08 dynabook-TECRA-A50-F wpa_supplicant[819]: rfkill: WLAN soft blocked
Apr  4 21:44:08 dynabook-TECRA-A50-F wpa_supplicant[819]: rfkill: WLAN soft blocked
Apr  4 21:44:08 dynabook-TECRA-A50-F systemd[1]: Started Load/Save RF Kill Switch Status.
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0409] dhcp4 (wlp1s0): canceled DHCP transaction
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0410] dhcp4 (wlp1s0): state changed bound -> done
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0413] dhcp6 (wlp1s0): canceled DHCP transaction
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0414] dhcp6 (wlp1s0): state changed bound -> done
Apr  4 21:44:08 dynabook-TECRA-A50-F whoopsie[1187]: [21:44:08] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.0445] manager: NetworkManager state is now DISCONNECTED
Apr  4 21:44:08 dynabook-TECRA-A50-F gnome-shell[1682]: An active wireless connection, in infrastructure mode, involves no access point?
Apr  4 21:44:08 dynabook-TECRA-A50-F geoclue[1268]: WiFi scan failed
Apr  4 21:44:08 dynabook-TECRA-A50-F wpa_supplicant[819]: nl80211: deinit ifname=p2p-dev-wlp1s0 disabled_11b_rates=0
Apr  4 21:44:08 dynabook-TECRA-A50-F dbus-daemon[785]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=786 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.1174] audit: op="radio-control" arg="wireless-enabled" pid=10642 uid=1000 result="success"
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.1177] manager: rfkill: Wi-Fi now disabled by radio killswitch
Apr  4 21:44:08 dynabook-TECRA-A50-F systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr  4 21:44:08 dynabook-TECRA-A50-F NetworkManager[786]: <info>  [1649123048.1199] device (p2p-dev-wlp1s0): state change: disconnected -> unavailable (reason 'supplicant-failed', sys-iface-state: 'managed')

---

### Post by chopra on 2022-04-04
update:
internet started working again (for now).
I'm not sure if this was a temporary thing or something else.

---

