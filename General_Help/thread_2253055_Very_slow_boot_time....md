---
title: "Very slow boot time..."
date: 2014-11-16
forum: General Help
---

### Post by Marcelo Ruiz on 2014-11-16
Hi,

My boot became really slow (Toshiba Qosmio X500, core i7, 8 Gb Ram, 1Gb nvidia GTS360M, 14.04 x64, nvidia 340, kernel 3.17.3)

This is the relevant portion of dmesg:

```

[   14.875558] nvidia: module license 'NVIDIA' taints kernel.
[   14.875562] Disabling lock debugging due to kernel taint
[   14.879713] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   14.885781] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.886293] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   14.886305] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.58  Fri Oct 31 17:40:28 PDT 2014
[   16.152270] init: failsafe main process (841) killed by TERM signal
[   17.887172] Bluetooth: RFCOMM TTY layer initialized
[   17.887183] Bluetooth: RFCOMM socket layer initialized
[   17.887193] Bluetooth: RFCOMM ver 1.11
[   18.121496] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.121500] Bluetooth: BNEP filters: protocol multicast
[   18.121507] Bluetooth: BNEP socket layer initialized
[   18.285575] init: avahi-cups-reload main process (1033) terminated with status 1
[   23.932834] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.949100] atl1c 0000:0b:00.0: irq 31 for MSI/MSI-X
[   23.962772] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.633804] init: udev-fallback-graphics main process (1278) terminated with status 1
[   25.416142] init: samba-ad-dc main process (1248) terminated with status 1
[   25.795774] wlan0: authenticate with 88:f7:c7:ce:f0:a3
[   25.805770] wlan0: send auth to 88:f7:c7:ce:f0:a3 (try 1/3)
[   25.807450] wlan0: authenticated
[   25.809516] wlan0: associate with 88:f7:c7:ce:f0:a3 (try 1/3)
[   25.812815] wlan0: RX AssocResp from 88:f7:c7:ce:f0:a3 (capab=0x411 status=0 aid=4)
[   25.814476] wlan0: associated
[   25.814484] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.221638] audit_printk_skb: 135 callbacks suppressed
[   26.221643] audit: type=1400 audit(1416187670.500:57): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cups-browsed" pid=1385 comm="apparmor_parser"
[   28.602255] audit: type=1400 audit(1416187672.880:58): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1713 comm="apparmor_parser"
[   31.623219] init: plymouth-upstart-bridge main process ended, respawning
[   31.629768] init: plymouth-upstart-bridge main process (1977) terminated with status 1
[   31.629784] init: plymouth-upstart-bridge main process ended, respawning
[   36.382568] nvidia 0000:01:00.0: irq 32 for MSI/MSI-X
[   50.658435] init: plymouth-stop pre-start process (2428) terminated with status 1
[  114.733513] toshiba_haps: Received event: 0x80
[  115.791821] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  118.309022] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  119.986763] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  163.058187] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  165.153630] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  166.309490] toshiba_haps: Received event: 0x80toshiba_haps: Received event: 0x80
[  167.259110] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  172.191123] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  556.951250] toshiba_haps: Received event: 0x81toshiba_haps: Received event: 0x80
[  558.597924] toshiba_haps: Received event: 0x81


```

Any ideas of what's going on here? Is toshiba_haps slowing my boot time?
Thanks!

---

### Post by pqwoerituytrueiwoq on 2014-11-16
install bootchart, maybe we can get something more helpful
and upload the image to imgur where it will not get resized and be unreadable

---

### Post by Marcelo Ruiz on 2014-11-19
@pqwoerituytrueiwoq

Thanks for your answer.
For some reason the lag I showed in my post doesn't show anymore...
I am using Linux Mint 17, and managed to install bootchart. Here is the image link:

[https://dl.dropboxusercontent.com/u/7707848/marcelo-qosmio-qiana-20141119-1.png]("https://dl.dropboxusercontent.com/u/7707848/marcelo-qosmio-qiana-20141119-1.png")

For some reason I am getting a very slow transition since the nVidia logo is shown in the screen until MDM is shown and a horribly slow transition from MDM until the desktop is shown. During all that time there is high I/O activity on the hard drive.

---

