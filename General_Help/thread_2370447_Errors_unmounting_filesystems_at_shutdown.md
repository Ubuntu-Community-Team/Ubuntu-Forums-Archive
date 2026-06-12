---
title: "Errors unmounting filesystems at shutdown"
date: 2017-09-03
forum: General Help
---

### Post by xquercus on 2017-09-03
These errors have been showing up on UbuntuGnome 17.04 since I installed it.  It looks like there are errors unmounting filesystems and shutting down LUKS.  It looks like fsck is being stopped at shutdown too.  Which makes me wonder if it's running because of a previous dirty shutdown.

I doubled *RateLimitBurst* in *journald.conf* in hopes of catching the 36 lines which get tossed at the end of the log to no avail.

```

Sep 03 12:05:37 lando NetworkManager[969]: <info>  [1504454737.0704] dhcp4 (wlp1s0): canceled DHCP transaction, DHCP client pid 1650
Sep 03 12:05:37 lando NetworkManager[969]: <info>  [1504454737.0704] dhcp4 (wlp1s0): state changed bound -> done
Sep 03 12:05:37 lando wpa_supplicant[1150]: p2p-dev-wlp1s0: CTRL-EVENT-TERMINATING
Sep 03 12:05:37 lando kernel: wlp1s0: deauthenticating from 68:7f:74:c6:87:44 by local choice (Reason: 3=DEAUTH_LEAVING)
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /dev/mapper/sda5_crypt.[/COLOR]
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /dev/dm-0.[/COLOR]
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /dev/disk/by-id/dm-name-sda5_crypt.[/COLOR]
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /sys/devices/virtual/block/dm-0.[/COLOR]
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /dev/disk/by-uuid/c305a90f-e4ab-4b80-be10-8bd079e81d47.[/COLOR]
Sep 03 12:05:37 lando systemd[1]: [COLOR="#FF0000"]Stopped (with error) /dev/disk/by-id/dm-uuid-CRYPT-LUKS1-3e575d48f4964ad98cedf0af941aae94-sda5_crypt.[/COLOR]
Sep 03 12:05:37 lando wpa_supplicant[1150]: wlp1s0: CTRL-EVENT-DISCONNECTED bssid=68:7f:74:c6:87:44 reason=3 locally_generated=1
Sep 03 12:05:37 lando NetworkManager[969]: ((devices/nm-device.c:9799)): assertion '<dropped>' failed
Sep 03 12:05:37 lando NetworkManager[969]: ((devices/nm-device.c:9799)): assertion '<dropped>' failed
Sep 03 12:05:37 lando NetworkManager[969]: <info>  [1504454737.0856] manager: NetworkManager state is now DISCONNECTED
Sep 03 12:05:37 lando dbus[942]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep 03 12:05:37 lando dbus[942]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.nm-dispatcher.service': Refusing activation, D-Bus is shutting down.
Sep 03 12:05:37 lando NetworkManager[969]: <info>  [1504454737.0896] exiting (success)
Sep 03 12:05:37 lando systemd[1]: Stopped Raise network interfaces.
Sep 03 12:05:37 lando systemd[1]: Stopped Network Manager.
Sep 03 12:05:37 lando systemd[1]: Stopping D-Bus System Message Bus...
Sep 03 12:05:37 lando systemd[1]: Stopped target Network (Pre).
Sep 03 12:05:37 lando systemd[1]: Stopped D-Bus System Message Bus.
Sep 03 12:05:37 lando wpa_supplicant[1150]: nl80211: deinit ifname=wlp1s0 disabled_11b_rates=0
Sep 03 12:05:37 lando wpa_supplicant[1150]: wlp1s0: CTRL-EVENT-TERMINATING
Sep 03 12:05:37 lando systemd[1]: Stopped WPA supplicant.
Sep 03 12:05:37 lando systemd[1]: Stopped Login Service.
Sep 03 12:05:37 lando systemd[1]: Stopped Thermal Daemon Service.
Sep 03 12:05:37 lando systemd[1]: Stopped target User and Group Name Lookups.
Sep 03 12:05:37 lando systemd[1]: Stopped target Basic System.
Sep 03 12:05:37 lando systemd[1]: Stopped Forward Password Requests to Plymouth Directory Watch.
Sep 03 12:05:37 lando systemd[1]: Stopped target Sockets.
Sep 03 12:05:37 lando systemd[1]: Closed ACPID Listen Socket.
Sep 03 12:05:37 lando systemd[1]: Closed UUID daemon activation socket.
Sep 03 12:05:37 lando systemd[1]: Closed Avahi mDNS/DNS-SD Stack Activation Socket.
Sep 03 12:05:37 lando systemd[1]: Closed Socket activation for snappy daemon.
Sep 03 12:05:37 lando systemd[1]: Closed CUPS Scheduler.
Sep 03 12:05:37 lando systemd[1]: Closed Syslog Socket.
Sep 03 12:05:37 lando systemd[1]: Stopped target Slices.
Sep 03 12:05:37 lando systemd[1]: Removed slice User and Session Slice.
Sep 03 12:05:37 lando systemd[1]: Stopped target Paths.
Sep 03 12:05:37 lando systemd[1]: Closed D-Bus System Message Bus Socket.
Sep 03 12:05:37 lando systemd[1]: Stopped target System Initialization.
Sep 03 12:05:37 lando systemd[1]: Stopping Load/Save Screen Backlight Brightness of backlight:intel_backlight...
Sep 03 12:05:37 lando systemd[1]: Stopped target Swap.
Sep 03 12:05:37 lando systemd[1]: Deactivating swap /swapfile...
Sep 03 12:05:37 lando systemd[1]: Stopping Update UTMP about System Boot/Shutdown...
Sep 03 12:05:37 lando systemd[1]: Stopping Network Time Synchronization...
Sep 03 12:05:37 lando systemd[1]: Stopping Load/Save Random Seed...
Sep 03 12:05:37 lando systemd[1]: Stopped target Encrypted Volumes.
Sep 03 12:05:37 lando systemd[1]: Stopped Forward Password Requests to Wall Directory Watch.
Sep 03 12:05:37 lando systemd[1]: Stopping Cryptography Setup for sda5_crypt...
Sep 03 12:05:37 lando systemd[1]: Stopped Apply Kernel Variables.
Sep 03 12:05:37 lando systemd[1]: Stopped Load Kernel Modules.
Sep 03 12:05:37 lando systemd[1]: Stopped Load/Save Screen Backlight Brightness of backlight:intel_backlight.
Sep 03 12:05:37 lando systemd[1]: Deactivated swap /swapfile.
Sep 03 12:05:37 lando systemd[1]: Stopped Load/Save Random Seed.
Sep 03 12:05:37 lando systemd[1]: Removed slice system-systemd\x2dbacklight.slice.
Sep 03 12:05:37 lando systemd[1]: Stopped Update UTMP about System Boot/Shutdown.
Sep 03 12:05:37 lando systemd[1]: Stopped Network Time Synchronization.
Sep 03 12:05:37 lando systemd[1]: Stopped Create Volatile Files and Directories.
Sep 03 12:05:37 lando systemd[1]: Stopped target Local File Systems.
Sep 03 12:05:37 lando systemd[1]: Unmounting /run/user/1000...
Sep 03 12:05:37 lando systemd[1]: Unmounting /boot/efi...
Sep 03 12:05:37 lando systemd[1]: Unmounted /run/user/1000.
Sep 03 12:05:37 lando systemd[1]: Unmounted /boot/efi.
Sep 03 12:05:37 lando systemd[1]: Stopped File System Check on /dev/disk/by-uuid/54C5-DE5D.
Sep 03 12:05:37 lando systemd[1]: Unmounting /boot...
Sep 03 12:05:37 lando systemd[1]: Unmounted /boot.
Sep 03 12:05:37 lando systemd[1]: Stopped File System Check on /dev/disk/by-uuid/63876870-b51c-4413-b9b5-a034b405a8d4.
Sep 03 12:05:37 lando systemd[1]: Removed slice system-systemd\x2dfsck.slice.
Sep 03 12:05:37 lando systemd[1]: Stopped target Local File Systems (Pre).
Sep 03 12:05:37 lando systemd[1]: Stopped Create Static Device Nodes in /dev.
Sep 03 12:05:37 lando systemd[1]: Stopped Remount Root and Kernel File Systems.
Sep 03 12:05:42 lando systemd-cryptsetup[2652]: [COLOR="#FF0000"]Failed to deactivate: Device or resource busy[/COLOR]
Sep 03 12:05:42 lando systemd[1]: systemd-cryptsetup@sda5_crypt.service: Control process exited, code=exited status=1
Sep 03 12:05:42 lando systemd[1]: Stopped Cryptography Setup for sda5_crypt.
Sep 03 12:05:42 lando systemd[1]: systemd-cryptsetup@sda5_crypt.service: Unit entered failed state.
Sep 03 12:05:42 lando systemd[1]: systemd-cryptsetup@sda5_crypt.service: Failed with result 'exit-code'.
Sep 03 12:05:42 lando systemd[1]: Reached target Unmount All Filesystems.
Sep 03 12:05:42 lando systemd[1]: Removed slice system-systemd\x2dcryptsetup.slice.
Sep 03 12:05:42 lando systemd[1]: Reached target Shutdown.
Sep 03 12:05:42 lando systemd[1]: Reached target Final Step.
Sep 03 12:05:42 lando systemd[1]: Starting Reboot...
Sep 03 12:05:42 lando systemd[1]: Shutting down.
Sep 03 12:05:42 lando kernel: systemd-shutdow: 36 output lines suppressed due to ratelimiting
Sep 03 12:05:42 lando systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Sep 03 12:05:42 lando systemd-journald[377]: Journal stopped

```

---

