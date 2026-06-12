---
title: "How to disable sleep?"
date: 2018-09-17
forum: General Help
---

### Post by ericandrewlewis on 2018-09-17
Hello! This is my first time posting in the forum. Thank you for any help, and apologies if I do anything wrong in this post.

I am attempting to use an Intel NUC running Ubuntu Desktop 16.04 as a web server.

I'd like to leave the computer on at the login screen. However when I do this, the Network Connection gets "disabled" after half an hour of inactivity, and I see messages like this in the syslog:

```
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7609] manager: sleep requested (sleeping: no  enabled: yes)
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7609] manager: sleeping...
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7622] manager: NetworkManager state is now ASLEEP
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7627] device (wlp0s12f0): state change: activated -> deactivating (reason 'sleeping') [100 110 37]
Sep 17 21:57:39 eric-NUC7CJYH whoopsie[1461]: [21:57:39] offline
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7667] device (wlp0s12f0): state change: deactivating -> disconnected (reason 'sleeping') [110 30 37]
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Withdrawing address record for fe80::f397:800b:4cdb:4dca on wlp0s12f0.
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Leaving mDNS multicast group on interface wlp0s12f0.IPv6 with address fe80::f397:800b:4cdb:4dca.
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Interface wlp0s12f0.IPv6 no longer relevant for mDNS.
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.7694] dns-mgr: Writing DNS information to /sbin/resolvconf
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Withdrawing address record for 192.168.1.100 on wlp0s12f0.
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Leaving mDNS multicast group on interface wlp0s12f0.IPv4 with address 192.168.1.100.
Sep 17 21:57:39 eric-NUC7CJYH avahi-daemon[805]: Interface wlp0s12f0.IPv4 no longer relevant for mDNS.
Sep 17 21:57:39 eric-NUC7CJYH dnsmasq[1400]: setting upstream servers from DBus
Sep 17 21:57:39 eric-NUC7CJYH kernel: [ 1937.960614] wlp0s12f0: deauthenticating from 9c:d3:6d:9e:4c:0e by local choice (Reason: 3=DEAUTH_LEAVING)
Sep 17 21:57:39 eric-NUC7CJYH wpa_supplicant[1040]: wlp0s12f0: CTRL-EVENT-DISCONNECTED bssid=9c:d3:6d:9e:4c:0e reason=3 locally_generated=1
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <warn>  [1537235859.7923] sup-iface[0x1746a20,wlp0s12f0]: connection disconnected (reason -3)
Sep 17 21:57:39 eric-NUC7CJYH dbus[807]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep 17 21:57:39 eric-NUC7CJYH systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 17 21:57:39 eric-NUC7CJYH NetworkManager[837]: <info>  [1537235859.8075] device (wlp0s12f0): state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Sep 

```

Is there a way to completely disable sleep, even in on the login screen to avoid this behavior?

---

### Post by Holger_Gehrke on 2018-09-18
Sure there is. You either run this for the used connection 
```

nmcli connection modify [COLOR=#ff0000]name-of-your-connection[/COLOR] 802-11-wireless.powersave disable

```
replacing the red part as needed. This will save the setting to the file for the connection, so you only need to run this once. Or you can set the default value for all connections by editing the file '/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf' and changing 'wifi.powersave = 3' to 'wifi.powersave = 2'. Might be a good idea to rename the file to 'default-wifi-powersafe-off.conf' afterwards so you can tell later what the value means ... (0=use default,1=ignore this setting,2=disable,3=enable). All files with extension .conf in that directory will be read by NetworkManager, regardless of the name.

Holger

---

### Post by ajgreeny on 2018-09-18
This appears to be a different solution suggested here, so if the one from HG is not successful have a look at [https://ubuntuforums.org/showthread.php?t=2283523](https://ubuntuforums.org/showthread.php?t=2283523) ; it may have nothing to do with the network connection so could be of no use for you.

---

### Post by ericandrewlewis on 2018-09-19
Thanks for the suggestion Holger, unfortunately that didn't stop the computer from going to sleep.

I did find this solution works:

```
sudo su
su lightdm -s /bin/bash
dbus-launch gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
exit
exit
```

From [SOLVED] Re: Disable system suspend at login screen - [https://ubuntuforums.org/showthread.php?t=2398526&p=13792071#post13792071](https://ubuntuforums.org/showthread.php?t=2398526&p=13792071#post13792071)

---

### Post by ajgreeny on 2018-09-20
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

