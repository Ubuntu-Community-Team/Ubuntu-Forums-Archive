---
title: "Hangs at startup"
date: 2007-12-07
forum: General Help
---

### Post by crevette on 2007-12-07
Hello,

since gutsy, the startup of ubuntu of my station to takes around 2 minutes; which it seems to be a bit long; 
after a look to dmesg I saw it hangs at several points

```

[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2135.141 MHz processor.
[   37.076490] Console: colour VGA+ 80x25
[   37.078579] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   37.078842] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   37.099443] Memory: 1027640k/1048128k available (2015k kernel code, 19784k reserved, 916k data, 364k init, 130624k highmem)

```

```

[   51.129201] NET: Registered protocol family 31
[   51.129240] Bluetooth: HCI device and connection manager initialized
[   51.129280] Bluetooth: HCI socket layer initialized
[   51.197736] Bluetooth: HCI USB driver ver 2.9
[   51.199993] usbcore: registered new interface driver hci_usb
[   51.250453] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   51.337067] ieee80211_init: failed to initialize WME (err=-17)
[   51.363359] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   51.363436] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   51.363497] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   51.363575] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   51.378725] wmaster0: Selected rate control algorithm 'simple'
[   51.473525] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   51.473611] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   51.611908] input: ImExPS/2 Logitech MX Mouse as /class/input/input3
[   81.542269] fuse init (API version 7.8)
[   81.557234] lp0: using parport0 (interrupt-driven).
[   81.687064] Adding 787176k swap on /dev/sda3.  Priority:-1 extents:1 across:787176k
[   81.884885] EXT3 FS on sda1, internal journal
[   82.418320] kjournald starting.  Commit interval 5 seconds

```

I did search on launchpad but didn't found something relevant.
Can you help me on that ?

I attached the dmesg log file.

---

### Post by loa on 2007-12-08
Have you tried some different kernels? You can try installing a few (search in synaptics for linux-kernel I think it is). You might also want to download one of the latest from kernel.org, compile it, and see if it happens there.

If other kernels work better, then you should report it as a bug on launchpad. Be sure to read [https://wiki.ubuntu.com/KernelTeamBugPolicies]("https://wiki.ubuntu.com/KernelTeamBugPolicies") and also look around at [https://wiki.ubuntu.com/Bugs]("https://wiki.ubuntu.com/Bugs") first, so you can prepare the bug report correctly.

Hope this could be some help.

---

