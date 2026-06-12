---
title: "Suspend only works when charging - 16.04"
date: 2017-10-18
forum: General Help
---

### Post by ndeubert on 2017-10-18
I have a Dell Precision 5510 with a fairly fresh install of Xubuntu 16.04, I have done a dist-upgrade since installing, but I don't believe resuming from suspend has ever worked consistently. If I suspend and resume with power plugged in then it always works fine, however if I suspend with power and then remove it, or suspend without power and then plug it in, or without power at all, then it always reboots when waking up. I have tried:

- Updated the bios to 1.4 per [http://www.dell.com/support/home/us/en/04/product-support/product/precision-m5510-workstation/drivers](http://www.dell.com/support/home/us/en/04/product-support/product/precision-m5510-workstation/drivers)
- Tried passing acpi settings into the kernel like acpi_osi="Linux" or acpi_sleep=nonvs"
- Tried the fixbacklight script from here: askubuntu.com/questions/820955/blank-screen-after-resume-dell-m5510-ubuntu-16-04
- Tried just making sure brightness was up all the way before suspending
- Tried nvidia drivers instead of nouveau
- Almost everything in this thread: askubuntu.com/questions/820955/blank-screen-after-resume-dell-m5510-ubuntu-16-04

Here is what I found at the end of /var/log/syslogd after booting back up:

```
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7538] manager: sleep requested (sleeping: no  enabled: yes)
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7539] manager: sleeping...
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7541] manager: NetworkManager state is now ASLEEP
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7547] device (wlp2s0): state change: activated -> deactivating (reason 'sleeping') [100 110 37]
Oct 13 00:10:24 dusseldorf whoopsie[1154]: [00:10:24] offline
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7652] device (wlp2s0): state change: deactivating -> disconnected (reason 'sleeping') [110 30 37]
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Withdrawing address record for fe80::ca4:844b:28fa:ee83 on wlp2s0.
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::ca4:844b:28fa:ee83.
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Interface wlp2s0.IPv6 no longer relevant for mDNS. 
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7977] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 5966
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.7978] dhcp4 (wlp2s0): state changed bound -> done
Oct 13 00:10:24 dusseldorf kernel: [ 5562.001601] wlp2s0: deauthenticating from 10:bf:48:53:0d:72 by local choice (Reason: 3=DEAUTH_LEAVING)
Oct 13 00:10:24 dusseldorf wpa_supplicant[1142]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=10:bf:48:53:0d:72 reason=3 locally_generated=1
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Withdrawing address record for 192.168.1.11 on wlp2s0.
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.1.11.
Oct 13 00:10:24 dusseldorf avahi-daemon[924]: Interface wlp2s0.IPv4 no longer relevant for mDNS. 
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.8118] dns-mgr: Writing DNS information to /sbin/resolvconf
Oct 13 00:10:24 dusseldorf dnsmasq[1456]: setting upstream servers from DBus
Oct 13 00:10:24 dusseldorf dbus[900]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <warn>  [1507867824.8699] sup-iface[0x19e7560,wlp2s0]: connection disconnected (reason -3)
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.8703] device (wlp2s0): supplicant interface state: completed -> disconnected
Oct 13 00:10:24 dusseldorf NetworkManager[930]: <info>  [1507867824.8717] device (wlp2s0): state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Oct 13 00:10:24 dusseldorf systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 13 00:10:24 dusseldorf dbus[900]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 13 00:10:24 dusseldorf systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 13 00:10:24 dusseldorf nm-dispatcher: req:1 'down' [wlp2s0]: new request (1 scripts)
Oct 13 00:10:24 dusseldorf nm-dispatcher: req:1 'down' [wlp2s0]: start running ordered scripts...
Oct 13 00:10:24 dusseldorf wpa_supplicant[1142]: nl80211: deinit ifname=p2p-dev-wlp2s0 disabled_11b_rates=0
Oct 13 00:10:24 dusseldorf systemd[1]: Reached target Sleep.
Oct 13 00:10:24 dusseldorf systemd[1]: Starting Suspend...
Oct 13 00:10:25 dusseldorf systemd-sleep[6217]: /lib/systemd/system-sleep/displaylink.sh: line 7: /tmp/PmMessagesPort_out: No such file or directory
Oct 13 00:10:25 dusseldorf wpa_supplicant[1142]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
Oct 13 00:10:29 dusseldorf whoopsie[1154]: [00:10:29] Cannot reach: https://daisy.ubuntu.com
Oct 13 00:10:29 dusseldorf whoopsie[1154]: [00:10:29] Cannot reach: https://daisy.ubuntu.com
Oct 13 00:10:35 dusseldorf systemd-sleep[6217]: Selected interface 'p2p-dev-wlp2s0'
Oct 13 00:10:35 dusseldorf systemd-sleep[6217]: 'SUSPEND' command timed out.
Oct 13 00:10:35 dusseldorf systemd-sleep[6218]: /lib/systemd/system-sleep/wpasupplicant failed with error code 254.
Oct 13 00:10:35 dusseldorf systemd-sleep[6217]: Suspending system...
Oct 13 00:11:11 dusseldorf rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="885" x-info="http://www.rsyslog.com"] start 
Oct 13 00:11:11 dusseldorf rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Oct 13 00:11:11 dusseldorf rsyslogd: rsyslogd's groupid changed to 108
Oct 13 00:11:11 dusseldorf rsyslogd: rsyslogd's userid changed to 104
```

Please let me know if you have any ideas, I really need to get suspend working because I travel a lot with this laptop and shutting down is very inconvenient.

---

### Post by ndeubert on 2017-10-20
Updated logs...

Here are some of the issues I now see in /var/log/syslogd when the system is going to sleep:

(I don't think this one matters because it is all over the log)
```
Oct 19 18:23:20 dusseldorf org.gtk.vfs.Daemon[1463]: ** (process:7800): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```

(I wouldn't think this would break suspend)

```
Oct 19 18:23:25 dusseldorf dhclient[10861]: receive_packet failed on enxd481d7504b08: Network is down
```

(Maybe?)
```
    Oct 19 18:23:25 dusseldorf kernel: [ 8281.352711] xhci_hcd 0000:3e:00.0: Host halt failed, -19
    Oct 19 18:23:25 dusseldorf kernel: [ 8281.352740] xhci_hcd 0000:3e:00.0: Host not accessible, reset failed.


    Oct 19 18:23:25 dusseldorf NetworkManager[891]: <error> [1508451805.5517] platform-linux: do-change-link[4]: failure changing link: failure 19 (No such device)
    Oct 19 18:23:25 dusseldorf NetworkManager[891]: <warn>  [1508451805.5518] device (enxd481d7504b08): failed to disable userspace IPv6LL address handling

    Oct 19 18:23:30 dusseldorf systemd-sleep[11638]: /lib/systemd/system-sleep/wpasupplicant failed with error code 254.

```

Here are some of the issues I see in the log when trying to resume:

```
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/udev/rules.d/71-nvidia.rules: No such file or directory
    ...
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/systemd/system/nvidia-persistenced.service: No such file or directory
    ...
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/modules/4.10.0-37-generic/updates/dkms/nvidia_375_modeset.ko: No such file or directory
    Oct 20 10:21:04 dusseldorf rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/modules/4.10.0-37-generic/updates/dkms/nvidia_375.ko: No such file or directory
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/modules/4.10.0-37-generic/updates/dkms/nvidia_375_drm.ko: No such file or directory
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/lib/modules/4.10.0-37-generic/updates/dkms/nvidia_375_uvm.ko: No such file or directory
    ...
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/sbin/create-uvm-dev-node: No such file or directory
    Oct 20 10:21:04 dusseldorf rsyslogd-2007: action 'action 10' suspended, next retry is Fri Oct 20 10:21:34 2017 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/etc/apparmor.d/usr.sbin.ntpd: No such file or directory
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/etc/apparmor.d/tunables/ntpd: No such file or directory
    Oct 20 10:21:04 dusseldorf ureadahead[299]: ureadahead:/etc/apparmor.d/local/usr.sbin.ntpd: No such file or directory
    Oct 20 10:21:04 dusseldorf systemd[1]: Created slice system-systemd\x2dbacklight.slice.
```

And the very last line of the resume before it reboots is:

```
   Oct 20 10:21:04 dusseldorf systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
```

---

