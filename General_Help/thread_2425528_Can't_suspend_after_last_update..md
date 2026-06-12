---
title: "Can't suspend after last update."
date: 2019-08-26
forum: General Help
---

### Post by leunam12 on 2019-08-26
Can't suspend, the computer suspends for a second or two and then comes back. Any help would be greatly appreciated. thanks

Asus Maximus VII Hero
Intel i7-4990K
Ubuntu 18.04
4.15.0-58-generic

```
{   33.088063] Suspending console(s) (use no_console_suspend to debug)
[   33.088839] e1000e: EEE TX LPI TIMER: 00000011
[   33.117271] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[   33.117372] sd 2:0:0:0: [sdb] Stopping disk
[   33.120026] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   33.120060] sd 0:0:0:0: [sda] Stopping disk
[   33.204856] dpm_run_callback(): usb_dev_suspend+0x0/0x20 returns -16
[   33.204862] PM: Device usb3 failed to suspend async: error -16
[   33.664986] PM: Some devices failed to suspend, or early wake event detected
[   33.665608] sd 0:0:0:0: [sda] Starting disk
[   33.665609] sd 2:0:0:0: [sdb] Starting disk
[   33.665893] input input2: event field not found
[   33.665895] input input2: event field not found
[   33.665896] input input2: event field not found
[   33.665897] input input2: event field not found
[   33.665898] input input2: event field not found
[   33.665899] input input2: event field not found
[   33.665899] input input2: event field not found
[   33.665901] input input2: event field not found
[   33.849021] OOM killer enabled.
[   33.849022] Restarting tasks ... done.
[   33.850556] PM: suspend exit
[   33.976013] usb 3-9: new full-speed USB device number 11 using xhci_hcd
[   33.978488] ata8: SATA link down (SStatus 0 SControl 300)
[   33.982703] ata7: SATA link down (SStatus 0 SControl 300)
[   33.990508] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   33.990656] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.998812] ata2.00: configured for UDMA/100
[   34.014336] ata1.00: configured for UDMA/133
[   34.104030] usb 3-9: device descriptor read/64, error -71
[   34.340021] usb 3-9: device descriptor read/64, error -71
[   34.576035] usb 3-9: new full-speed USB device number 12 using xhci_hcd
[   34.704006] usb 3-9: device descriptor read/64, error -71
[   34.940022] usb 3-9: device descriptor read/64, error -71
[   35.048050] usb usb3-port9: attempt power cycle
[   35.700028] usb 3-9: new full-speed USB device number 13 using xhci_hcd
[   35.700150] usb 3-9: Device not responding to setup address.
[   35.908144] usb 3-9: Device not responding to setup address.
[   36.116042] usb 3-9: device not accepting address 13, error -71
[   36.244027] usb 3-9: new full-speed USB device number 14 using xhci_hcd
[   36.244147] usb 3-9: Device not responding to setup address.
[   36.452157] usb 3-9: Device not responding to setup address.
[   36.660041] usb 3-9: device not accepting address 14, error -71
[   36.660100] usb usb3-port9: unable to enumerate USB device
[   38.654229] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  141.705402] usb 3-8: USB disconnect, device number 3
[  150.419994] PM: suspend entry (deep)
[  150.419996] PM: Syncing filesystems ... done.
[  150.420763] Freezing user space processes ... (elapsed 0.029 seconds) done.
[  150.450520] OOM killer disabled.
[  150.450521] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  150.451755] Suspending console(s) (use no_console_suspend to debug)
[  150.452283] e1000e: EEE TX LPI TIMER: 00000011
[  150.479842] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  150.479843] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  150.479865] sd 0:0:0:0: [sda] Stopping disk
[  150.479968] sd 2:0:0:0: [sdb] Stopping disk
[  150.510873] dpm_run_callback(): usb_dev_suspend+0x0/0x20 returns -16
[  150.510876] PM: Device usb3 failed to suspend async: error -16
[  151.027319] PM: Some devices failed to suspend, or early wake event detected
[  151.027587] sd 0:0:0:0: [sda] Starting disk
[  151.027603] sd 2:0:0:0: [sdb] Starting disk
[  151.028001] input input2: event field not found
[  151.028002] input input2: event field not found
[  151.028002] input input2: event field not found
[  151.028003] input input2: event field not found
[  151.028004] input input2: event field not found
[  151.028004] input input2: event field not found
[  151.028005] input input2: event field not found
[  151.028006] input input2: event field not found
[  151.210928] OOM killer enabled.
[  151.210929] Restarting tasks ... done.
[  151.212427] PM: suspend exit
[  151.337716] usb 3-9: new full-speed USB device number 15 using xhci_hcd
[  151.340423] ata7: SATA link down (SStatus 0 SControl 300)
[  151.340464] ata8: SATA link down (SStatus 0 SControl 300)
[  151.352322] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  151.356318] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  151.364509] ata2.00: configured for UDMA/100
[  151.376153] ata1.00: configured for UDMA/133
[  151.469625] usb 3-9: device descriptor read/64, error -71
[  151.705467] usb 3-9: device descriptor read/64, error -71
[  151.941239] usb 3-9: new full-speed USB device number 16 using xhci_hcd
[  152.069179] usb 3-9: device descriptor read/64, error -71
[  152.304985] usb 3-9: device descriptor read/64, error -71
[  152.412941] usb usb3-port9: attempt power cycle
[  153.076315] usb 3-9: new full-speed USB device number 17 using xhci_hcd
[  153.076447] usb 3-9: Device not responding to setup address.
[  153.284306] usb 3-9: Device not responding to setup address.
[  153.492004] usb 3-9: device not accepting address 17, error -71
[  153.619837] usb 3-9: new full-speed USB device number 18 using xhci_hcd
[  153.619962] usb 3-9: Device not responding to setup address.
[  153.827751] usb 3-9: Device not responding to setup address.
[  154.035503] usb 3-9: device not accepting address 18, error -71
[  154.035550] usb usb3-port9: unable to enumerate USB device
[  155.580699] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  268.846352] PM: suspend entry (deep)
[  268.846353] PM: Syncing filesystems ... done.
[  268.852100] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  268.853765] OOM killer disabled.
[  268.853766] Freezing remaining freezable tasks ... (elapsed 0.000 seconds) done.
[  268.854758] Suspending console(s) (use no_console_suspend to debug)
[  268.855175] e1000e: EEE TX LPI TIMER: 00000011
[  268.962876] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  268.963004] sd 2:0:0:0: [sdb] Stopping disk
[  268.966929] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  268.966961] sd 0:0:0:0: [sda] Stopping disk
[  268.975274] dpm_run_callback(): usb_dev_suspend+0x0/0x20 returns -16
[  268.975276] PM: Device usb3 failed to suspend async: error -16
[  269.509949] PM: Some devices failed to suspend, or early wake event detected
[  269.510333] sd 0:0:0:0: [sda] Starting disk
[  269.510336] sd 2:0:0:0: [sdb] Starting disk
[  269.510727] input input2: event field not found
[  269.510728] input input2: event field not found
[  269.510728] input input2: event field not found
[  269.510729] input input2: event field not found
[  269.510730] input input2: event field not found
[  269.510730] input input2: event field not found
[  269.510731] input input2: event field not found
[  269.510731] input input2: event field not found
[  269.693134] OOM killer enabled.
[  269.693134] Restarting tasks ... done.
[  269.694639] PM: suspend exit
[  269.694688] PM: suspend entry (s2idle)
[  269.694690] PM: Syncing filesystems ... 
[  269.820198] usb 3-9: new full-speed USB device number 19 using xhci_hcd
[  269.822594] ata7: SATA link down (SStatus 0 SControl 300)
[  269.826529] ata8: SATA link down (SStatus 0 SControl 300)
[  269.834523] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  269.834538] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  269.842556] ata2.00: configured for UDMA/100
[  269.858351] ata1.00: configured for UDMA/133
[  269.866976] done.
[  269.867139] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  269.868338] OOM killer disabled.
[  269.868338] Freezing remaining freezable tasks ... 
[  269.948400] usb 3-9: device descriptor read/64, error -71
[  270.184748] usb 3-9: device descriptor read/64, error -71
[  270.421100] usb 3-9: new full-speed USB device number 20 using xhci_hcd
[  270.549303] usb 3-9: device descriptor read/64, error -71
[  270.785657] usb 3-9: device descriptor read/64, error -71
[  270.893829] usb usb3-port9: attempt power cycle
[  271.546780] usb 3-9: new full-speed USB device number 21 using xhci_hcd
[  271.546884] usb 3-9: Device not responding to setup address.
[  271.755189] usb 3-9: Device not responding to setup address.
[  271.963406] usb 3-9: device not accepting address 21, error -71
[  272.091588] usb 3-9: new full-speed USB device number 22 using xhci_hcd
[  272.091705] usb 3-9: Device not responding to setup address.
[  272.300011] usb 3-9: Device not responding to setup address.
[  272.508182] usb 3-9: device not accepting address 22, error -71
[  272.508220] usb usb3-port9: unable to enumerate USB device
[  272.515633] (elapsed 2.643 seconds) done.
[  272.515637] Suspending console(s) (use no_console_suspend to debug)
[  272.516485] e1000e: EEE TX LPI TIMER: 00000011
[  272.544514] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  272.544515] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  272.544562] sd 0:0:0:0: [sda] Stopping disk
[  272.544618] sd 2:0:0:0: [sdb] Stopping disk
[  272.576616] dpm_run_callback(): usb_dev_suspend+0x0/0x20 returns -16
[  272.576619] PM: Device usb3 failed to suspend async: error -16
[  273.101113] PM: Some devices failed to suspend, or early wake event detected
[  273.101442] sd 0:0:0:0: [sda] Starting disk
[  273.101445] sd 2:0:0:0: [sdb] Starting disk
[  273.101940] input input2: event field not found
[  273.101941] input input2: event field not found
[  273.101942] input input2: event field not found
[  273.101942] input input2: event field not found
[  273.101943] input input2: event field not found
[  273.101944] input input2: event field not found
[  273.101944] input input2: event field not found
[  273.101945] input input2: event field not found
[  273.286197] OOM killer enabled.
[  273.286198] Restarting tasks ... done.
[  273.287766] PM: suspend exit
[  273.407038] e1000e: eno1 NIC Link is Down
[  273.413467] usb 3-9: new full-speed USB device number 23 using xhci_hcd
[  273.415763] ata8: SATA link down (SStatus 0 SControl 300)
[  273.419708] ata7: SATA link down (SStatus 0 SControl 300)
[  273.426586] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  273.426606] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  273.434668] ata2.00: configured for UDMA/100
[  273.450426] ata1.00: configured for UDMA/133
[  273.456947] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  273.541657] usb 3-9: device descriptor read/64, error -71
[  273.641894] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  273.781967] usb 3-9: device descriptor read/64, error -71
[  274.018289] usb 3-9: new full-speed USB device number 24 using xhci_hcd
[  274.146482] usb 3-9: device descriptor read/64, error -71
[  274.382788] usb 3-9: device descriptor read/64, error -71
[  274.490935] usb usb3-port9: attempt power cycle
[  275.143824] usb 3-9: new full-speed USB device number 25 using xhci_hcd
[  275.143943] usb 3-9: Device not responding to setup address.
[  275.352215] usb 3-9: Device not responding to setup address.
[  275.560389] usb 3-9: device not accepting address 25, error -71
[  275.688507] usb 3-9: new full-speed USB device number 26 using xhci_hcd
[  275.688611] usb 3-9: Device not responding to setup address.
[  275.896903] usb 3-9: Device not responding to setup address.
[  276.105057] usb 3-9: device not accepting address 26, error -71
[  276.105095] usb usb3-port9: unable to enumerate USB device
[  276.531825] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  276.531857] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
rivasdom@RivasPC-2:~$ 


```

---

