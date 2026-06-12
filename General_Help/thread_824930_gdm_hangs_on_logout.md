---
title: "gdm hangs on logout"
date: 2008-06-10
forum: General Help
---

### Post by cszikszoy on 2008-06-10
Hello,

I have a problem when trying to logout of my gnome session.  This happens when I try to shutdown my computer.  When I click the quit button, then shut down, all of the processes are killed, and the panels disappear.  Then the computer just hangs there, only showing my desktop background.  When this happens I can press ctrl+alt+backspace and then the computer will continue to shutdown.

This really isn't too fatal of an error, but it's just a pain to always click shutdown and then kill GDM with ctrl+alt+bksp.

Here's the only abnormal thing that I found in the shutdown process:
```
Jun 10 02:29:31 chris-laptop gdm[24294]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

I've also attached the entire syslog of the shutdown process:
```
Jun 10 02:25:59 chris-laptop kernel: [ 6182.853530] CPU0 attaching NULL sched-domain.
Jun 10 02:25:59 chris-laptop kernel: [ 6182.853539] CPU1 attaching NULL sched-domain.
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881657] CPU0 attaching sched-domain:
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881666]  domain 0: span 03
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881669]   groups: 01 02
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881675]   domain 1: span 03
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881688]    groups: 03
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881693] CPU1 attaching sched-domain:
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881695]  domain 0: span 03
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881698]   groups: 02 01
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881703]   domain 1: span 03
Jun 10 02:25:59 chris-laptop kernel: [ 6182.881706]    groups: 03
Jun 10 02:29:31 chris-laptop gdm[24294]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun 10 02:29:32 chris-laptop init: tty4 main process (4726) killed by TERM signal
Jun 10 02:29:32 chris-laptop init: tty5 main process (4727) killed by TERM signal
Jun 10 02:29:32 chris-laptop init: tty2 main process (4729) killed by TERM signal
Jun 10 02:29:32 chris-laptop init: tty3 main process (4730) killed by TERM signal
Jun 10 02:29:32 chris-laptop init: tty6 main process (4731) killed by TERM signal
Jun 10 02:29:32 chris-laptop init: tty1 main process (6021) killed by TERM signal
Jun 10 02:29:32 chris-laptop kernel: [ 6393.863021] printk: 6 messages suppressed.
Jun 10 02:29:32 chris-laptop kernel: [ 6393.863033] usplash[8275] general protection eip:b7f4182b esp:bfa2e248 error:0
Jun 10 02:29:33 chris-laptop gdm[8317]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed 
Jun 10 02:29:33 chris-laptop last message repeated 2 times
Jun 10 02:29:33 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:33 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jun 10 02:29:33 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:33 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jun 10 02:29:34 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: gdm_slave_send: Can't open fifo! 
Jun 10 02:29:34 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: gdm_auth_secure_display: Cannot safely open  
Jun 10 02:29:34 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key daemon/ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh 
Jun 10 02:29:34 chris-laptop gdm[8317]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 10 02:29:34 chris-laptop gdm[8317]: WARNING: Request for invalid configuration key daemon/ConsoleNotify=true 
Jun 10 02:29:35 chris-laptop avahi-daemon[5185]: Got SIGTERM, quitting.
Jun 10 02:29:35 chris-laptop avahi-daemon[5185]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.52.
Jun 10 02:29:35 chris-laptop kernel: [ 6396.951672] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Jun 10 02:29:36 chris-laptop NetworkManager: <debug> [1213090175.995721] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_18_8b_a6_b9_92'). 
Jun 10 02:29:36 chris-laptop NetworkManager: <info>  Deactivating device eth0. 
Jun 10 02:29:36 chris-laptop kernel: [ 6397.416689] ndiswrapper: device wlan0 removed
Jun 10 02:29:36 chris-laptop kernel: [ 6397.416726] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Jun 10 02:29:36 chris-laptop kernel: [ 6397.416878] usbcore: deregistering interface driver ndiswrapper
Jun 10 02:29:36 chris-laptop dhclient: receive_packet failed on wlan0: Network is down
Jun 10 02:29:36 chris-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jun 10 02:29:36 chris-laptop kernel: [ 6397.601914] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jun 10 02:29:36 chris-laptop NetworkManager: <debug> [1213090176.666153] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jun 10 02:29:36 chris-laptop NetworkManager: <debug> [1213090176.666249] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jun 10 02:29:36 chris-laptop NetworkManager: <debug> [1213090176.666289] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_18_f3_d8_f5_7e'). 
Jun 10 02:29:36 chris-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jun 10 02:29:36 chris-laptop kernel: [ 6399.739237] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Jun 10 02:29:36 chris-laptop kernel: [ 6399.739938] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 10 02:29:36 chris-laptop kernel: [ 6399.740014] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Jun 10 02:29:36 chris-laptop kernel: [ 6399.745311] ndiswrapper: using IRQ 17
Jun 10 02:29:37 chris-laptop kernel: [ 6400.128474] wlan0: ethernet device 00:18:f3:d8:f5:7e using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Jun 10 02:29:37 chris-laptop kernel: [ 6400.129117] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jun 10 02:29:37 chris-laptop kernel: [ 6400.150454] usbcore: registered new interface driver ndiswrapper
Jun 10 02:29:37 chris-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jun 10 02:29:37 chris-laptop kernel: [ 6398.283492] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 10 02:29:37 chris-laptop kernel: [ 6398.341790] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Jun 10 02:29:37 chris-laptop kernel: [ 6398.341836] b44.c:v2.0
Jun 10 02:29:37 chris-laptop kernel: [ 6398.362605] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:18:8b:a6:b9:92
Jun 10 02:29:37 chris-laptop NetworkManager: <debug> [1213090177.613702] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_18_f3_d8_f5_7e'). 
Jun 10 02:29:37 chris-laptop kernel: [ 6400.673643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jun 10 02:29:37 chris-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jun 10 02:29:37 chris-laptop NetworkManager: <debug> [1213090177.639927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jun 10 02:29:37 chris-laptop NetworkManager: <debug> [1213090177.640601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jun 10 02:29:37 chris-laptop NetworkManager: <debug> [1213090177.641216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_18_8b_a6_b9_92'). 
Jun 10 02:29:37 chris-laptop kernel: [ 6400.699007] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun 10 02:29:37 chris-laptop NetworkManager: <info>  Deactivating device eth0. 
Jun 10 02:29:38 chris-laptop kernel: [ 6399.826189] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 10 02:29:40 chris-laptop exiting on signal 15
```

Any help is greatly appreciated.

Thanks,
-Chris

---

### Post by GrouchoMarx on 2008-06-11
I just solved a similar problem by wiping .gnome2 in the user account that was affected (you can move it temporarily if you don't want to wipe it).

---

### Post by cszikszoy on 2008-06-11
I'll try that and see if it helps.  I think my problem is related to this bug report:

[https://bugs.launchpad.net/debian/+source/keytouch/+bug/186713](https://bugs.launchpad.net/debian/+source/keytouch/+bug/186713)

It has to do with keytouch being installed.

---

