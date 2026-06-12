---
title: "Can't seem to find laptop webcam"
date: 2013-01-18
forum: General Help
---

### Post by userfriendly1992 on 2013-01-18
I am using a Gateway LT4010u netbook. I first noticed this when I tried to Skype and the option for Video Call was disabled.

How do I get my Laptop's webcam up and running so I can use Skype and take pictures with my webcam?

---

### Post by userfriendly1992 on 2013-01-18
I am using a Gateway LT4010u netbook. I first noticed this when I tried to Skype and the option for Video Call was disabled.

How do I get my Laptop's webcam up and running so I can use Skype and take pictures with my webcam?

---

### Post by mörgæs on 2013-01-18
Please don't double-post.
Merged.

---

### Post by userfriendly1992 on 2013-01-18
Apologies.

Back to the post though, my webcam is working on Cheese, but with Skype its still refusing to let me place a video call. Anyone know a solution to this?

---

### Post by xc3RnbFO8P on 2013-01-18
In terminal show the output of:
> dmesg
and
> lsusb

---

### Post by userfriendly1992 on 2013-01-18
Output of dmesg:

```
[ 9998.548355] PM: Saving platform NVS memory
[ 9998.554806] Disabling non-boot CPUs ...
[ 9998.658159] CPU 1 is now offline
[ 9998.762064] CPU 2 is now offline
[ 9998.865942] CPU 3 is now offline
[ 9998.866821] Extended CMOS year: 2000
[ 9998.866983] ACPI: Low-level resume complete
[ 9998.867051] PM: Restoring platform NVS memory
[ 9998.868237] CPU0: Thermal monitoring handled by SMI
[ 9998.868327] Extended CMOS year: 2000
[ 9998.868423] Enabling non-boot CPUs ...
[ 9998.868723] Booting Node 0 Processor 1 APIC 0x1
[ 9998.868728] smpboot cpu 1: start_ip = 99000
[ 9998.879669] Calibrating delay loop (skipped) already calibrated this CPU
[ 9998.879702] CPU1: Thermal monitoring handled by SMI
[ 9998.900345] NMI watchdog enabled, takes one hw-pmu counter.
[ 9998.900911] CPU1 is up
[ 9998.901146] Booting Node 0 Processor 2 APIC 0x2
[ 9998.901151] smpboot cpu 2: start_ip = 99000
[ 9998.912109] Calibrating delay loop (skipped) already calibrated this CPU
[ 9998.912139] CPU2: Thermal monitoring handled by SMI
[ 9998.933222] NMI watchdog enabled, takes one hw-pmu counter.
[ 9998.933865] CPU2 is up
[ 9998.934181] Booting Node 0 Processor 3 APIC 0x3
[ 9998.934186] smpboot cpu 3: start_ip = 99000
[ 9998.945121] Calibrating delay loop (skipped) already calibrated this CPU
[ 9998.945150] CPU3: Thermal monitoring handled by SMI
[ 9998.966833] NMI watchdog enabled, takes one hw-pmu counter.
[ 9998.967522] CPU3 is up
[ 9998.969052] ACPI: Waking up from system sleep state S3
[ 9998.971430] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 9998.971483] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 9998.971520] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 9998.971600] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 9998.971637] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 9998.971713] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 9998.971750] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 9998.971841] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9998.971912] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[ 9998.971957] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9998.972013] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[ 9998.972058] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9998.972114] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[ 9998.972158] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9998.972213] uhci_hcd 0000:00:1d.3: wake-up capability disabled by ACPI
[ 9998.972269] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 9998.972334] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[ 9998.972346] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9998.972366] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 9998.972385] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[ 9998.972520] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 9998.972670] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 9998.972766] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 9998.972781] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 9998.972876] rts_pstor 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9998.973136] PM: early resume of devices complete after 1.928 msecs
[ 9998.973508] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 9998.973527] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 9998.973626] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 9998.973749] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9998.973766] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 9998.973810] usb usb2: root hub lost power or was reset
[ 9998.973846] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 9998.973865] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 9998.973907] usb usb3: root hub lost power or was reset
[ 9998.973943] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 9998.973959] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 9998.974003] usb usb4: root hub lost power or was reset
[ 9998.974035] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 9998.974052] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 9998.974097] usb usb5: root hub lost power or was reset
[ 9998.974133] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9998.974150] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 9998.974215] pci 0000:00:1e.0: setting latency timer to 64
[ 9998.974253] ahci 0000:00:1f.2: setting latency timer to 64
[ 9998.974378] r8169 0000:01:00.0: wake-up capability disabled by ACPI
[ 9998.974395] r8169 0000:01:00.0: PME# disabled
[ 9998.974657] Ready to resume
[ 9998.974683] rts_pstor 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 9998.974697] rts_pstor 0000:03:00.0: setting latency timer to 64
[ 9998.974708] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[ 9998.982322] sd 0:0:0:0: [sda] Starting disk
[ 9998.984960] Extended CMOS year: 2000
[ 9999.099251] PM: resume of drv:hub dev:4-0:1.0 complete after 117.484 msecs
[ 9999.099271] PM: resume of drv: dev:ep_00 complete after 117.531 msecs
[ 9999.099291] PM: resume of drv: dev:ep_00 complete after 117.490 msecs
[ 9999.099308] PM: resume of drv: dev:ep_81 complete after 117.541 msecs
[ 9999.099319] PM: resume of drv:hub dev:3-0:1.0 complete after 117.652 msecs
[ 9999.099340] PM: resume of drv: dev:ep_81 complete after 117.655 msecs
[ 9999.099403] PM: resume of drv:hub dev:5-0:1.0 complete after 117.425 msecs
[ 9999.099437] PM: resume of drv: dev:ep_00 complete after 117.313 msecs
[ 9999.099459] PM: resume of drv: dev:ep_81 complete after 117.413 msecs
[ 9999.103228] PM: resume of drv:hub dev:1-0:1.0 complete after 123.812 msecs
[ 9999.103256] PM: resume of drv: dev:ep_00 complete after 123.809 msecs
[ 9999.103317] PM: resume of drv:hub dev:2-0:1.0 complete after 123.843 msecs
[ 9999.103325] PM: resume of drv: dev:ep_81 complete after 123.889 msecs
[ 9999.103340] PM: resume of drv: dev:ep_00 complete after 121.718 msecs
[ 9999.103366] PM: resume of drv: dev:ep_81 complete after 121.754 msecs
[ 9999.156067] PM: resume of drv:r8169 dev:0000:01:00.0 complete after 181.880 msecs
[ 9999.175322] PM: resume of drv:rts_pstor dev:0000:03:00.0 complete after 200.851 msecs
[ 9999.175359] PM: resume of drv:scsi dev:host4 complete after 192.745 msecs
[ 9999.175410] PM: resume of drv:scsi_host dev:host4 complete after 192.737 msecs
[ 9999.175418] PM: resume of drv:scsi dev:target4:0:0 complete after 192.679 msecs
[ 9999.175451] PM: resume of drv:sd dev:4:0:0:0 complete after 192.661 msecs
[ 9999.175476] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 192.625 msecs
[ 9999.215518] usb 1-3: reset high-speed USB device number 2 using ehci_hcd
[ 9999.291108] ata2: SATA link down (SStatus 0 SControl 300)
[ 9999.454398] PM: resume of drv:uvcvideo dev:1-3:1.0 complete after 472.280 msecs
[ 9999.454406] PM: resume of drv:uvcvideo dev:1-3:1.1 complete after 472.173 msecs
[ 9999.454424] PM: resume of drv: dev:ep_82 complete after 472.250 msecs
[ 9999.454447] PM: resume of drv: dev:ep_00 complete after 472.155 msecs
[10001.361171] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[10001.365908] ata1.00: configured for UDMA/133
[10001.387282] PM: resume of drv:sd dev:0:0:0:0 complete after 2407.224 msecs
[10001.387315] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2407.141 msecs
[10001.387327] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2404.540 msecs
[10001.393069] PM: resume of devices complete after 2422.147 msecs
[10001.393329] PM: resume devices took 2.424 seconds
[10001.393407] PM: Finishing wakeup.
[10001.393411] Restarting tasks ... done.
[10006.663052] r8169 0000:01:00.0: eth0: link down
[10006.663676] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10007.178331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10012.146349] wlan0: authenticate with 74:9d:dc:9a:c1:59 (try 1)
[10012.148146] wlan0: authenticated
[10012.165587] wlan0: associate with 74:9d:dc:9a:c1:59 (try 1)
[10012.168020] wlan0: RX AssocResp from 74:9d:dc:9a:c1:59 (capab=0x431 status=0 aid=1)
[10012.168033] wlan0: associated
[10012.169858] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10012.170289] cfg80211: Calling CRDA for country: US
[10013.603242] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[10013.603258] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603269] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[10013.603280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603290] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[10013.603301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603310] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[10013.603321] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603330] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[10013.603341] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603349] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[10013.603359] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603368] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[10013.603379] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603389] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[10013.603399] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603409] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[10013.603420] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603430] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[10013.603441] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603451] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[10013.603461] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603470] cfg80211: Disabling freq 2467 MHz
[10013.603476] cfg80211: Disabling freq 2472 MHz
[10013.603482] cfg80211: Disabling freq 2484 MHz
[10013.603494] cfg80211: Regulatory domain changed to country: US
[10013.603502] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[10013.603512] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[10013.603522] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[10013.603532] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10013.603541] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10013.603551] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10013.603561] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[10023.300446] wlan0: no IPv6 routers present
[13773.003715] wlan0: deauthenticating from 74:9d:dc:9a:c1:59 by local choice (reason=3)
[13773.104216] cfg80211: All devices are disconnected, going to restore regulatory settings
[13773.104232] cfg80211: Restoring regulatory settings
[13773.104297] cfg80211: Calling CRDA to update world regulatory domain
[13774.688389] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[13774.688399] cfg80211: World regulatory domain updated:
[13774.688404] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13774.688412] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13774.688419] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13774.688425] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13774.688432] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13774.688439] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13781.279342] PM: Syncing filesystems ... done.
[13781.283414] PM: Preparing system for mem sleep
[13781.283456] Freezing user space processes ... (elapsed 0.01 seconds) done.
[13781.301654] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[13781.317664] PM: Entering mem sleep
[13781.317934] Suspending console(s) (use no_console_suspend to debug)
[13781.318443] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[13781.318825] sd 0:0:0:0: [sda] Stopping disk
[13781.368376] Ready to suspend
[13781.405566] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[13781.405603] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[13781.405658] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[13781.405671] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[13781.409409] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[13781.573821] PM: suspend of drv:sd dev:0:0:0:0 complete after 255.628 msecs
[13781.573859] PM: suspend of drv:scsi dev:target0:0:0 complete after 255.598 msecs
[13781.573915] PM: suspend of drv:scsi dev:host0 complete after 205.812 msecs
[13781.589255] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 220.865 msecs
[13781.629357] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[13781.645184] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 276.146 msecs
[13782.364619] rts_pstor 0000:03:00.0: PCI INT A disabled
[13782.380518] PM: suspend of drv:rts_pstor dev:0000:03:00.0 complete after 1013.101 msecs
[13782.380551] PM: suspend of drv:pcieport dev:0000:00:1c.2 complete after 1012.329 msecs
[13782.380620] PM: suspend of drv: dev:pci0000:00 complete after 1012.148 msecs
[13782.380647] PM: suspend of devices complete after 1063.439 msecs
[13782.380655] PM: suspend devices took 1.064 seconds
[13782.396745] r8169 0000:01:00.0: PME# enabled
[13782.396772] r8169 0000:01:00.0: wake-up capability enabled by ACPI
[13782.412647] ehci_hcd 0000:00:1d.7: PME# enabled
[13782.412748] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[13782.428557] uhci_hcd 0000:00:1d.3: wake-up capability enabled by ACPI
[13782.428665] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[13782.428771] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[13782.428876] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[13782.429163] PM: late suspend of devices complete after 48.544 msecs
[13782.429206] ACPI: Preparing to enter system sleep state S3
[13782.430514] PM: Saving platform NVS memory
[13782.436897] Disabling non-boot CPUs ...
[13782.540343] CPU 1 is now offline
[13782.644244] CPU 2 is now offline
[13782.748155] CPU 3 is now offline
[13782.748998] Extended CMOS year: 2000
[13782.749160] ACPI: Low-level resume complete
[13782.749229] PM: Restoring platform NVS memory
[13782.750332] CPU0: Thermal monitoring handled by SMI
[13782.750429] Extended CMOS year: 2000
[13782.750525] Enabling non-boot CPUs ...
[13782.750824] Booting Node 0 Processor 1 APIC 0x1
[13782.750829] smpboot cpu 1: start_ip = 99000
[13782.761769] Calibrating delay loop (skipped) already calibrated this CPU
[13782.761802] CPU1: Thermal monitoring handled by SMI
[13782.782598] NMI watchdog enabled, takes one hw-pmu counter.
[13782.783179] CPU1 is up
[13782.783412] Booting Node 0 Processor 2 APIC 0x2
[13782.783417] smpboot cpu 2: start_ip = 99000
[13782.794354] Calibrating delay loop (skipped) already calibrated this CPU
[13782.794383] CPU2: Thermal monitoring handled by SMI
[13782.815465] NMI watchdog enabled, takes one hw-pmu counter.
[13782.816112] CPU2 is up
[13782.816427] Booting Node 0 Processor 3 APIC 0x3
[13782.816432] smpboot cpu 3: start_ip = 99000
[13782.827368] Calibrating delay loop (skipped) already calibrated this CPU
[13782.827396] CPU3: Thermal monitoring handled by SMI
[13782.849006] NMI watchdog enabled, takes one hw-pmu counter.
[13782.849722] CPU3 is up
[13782.851268] ACPI: Waking up from system sleep state S3
[13782.854342] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[13782.854398] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[13782.854437] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[13782.854521] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[13782.854559] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[13782.854640] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[13782.854679] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[13782.854774] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[13782.854842] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[13782.854889] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[13782.854947] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[13782.854993] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[13782.855049] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[13782.855095] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[13782.855151] uhci_hcd 0000:00:1d.3: wake-up capability disabled by ACPI
[13782.855210] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[13782.855276] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[13782.855288] ehci_hcd 0000:00:1d.7: PME# disabled
[13782.855309] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[13782.855329] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[13782.855471] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[13782.855629] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[13782.855730] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[13782.855745] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[13782.855845] rts_pstor 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[13782.856108] PM: early resume of devices complete after 1.937 msecs
[13782.856291] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[13782.856301] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[13782.856308] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[13782.856316] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[13782.856377] usb usb2: root hub lost power or was reset
[13782.856419] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[13782.856434] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[13782.856455] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[13782.856489] usb usb3: root hub lost power or was reset
[13782.856537] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[13782.856553] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[13782.856602] pci 0000:00:1e.0: setting latency timer to 64
[13782.856607] usb usb5: root hub lost power or was reset
[13782.856653] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[13782.856677] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[13782.856722] Ready to resume
[13782.856734] usb usb4: root hub lost power or was reset
[13782.856776] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[13782.856794] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[13782.861680] ahci 0000:00:1f.2: setting latency timer to 64
[13782.861697] r8169 0000:01:00.0: wake-up capability disabled by ACPI
[13782.861715] rts_pstor 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[13782.861728] r8169 0000:01:00.0: PME# disabled
[13782.861741] rts_pstor 0000:03:00.0: setting latency timer to 64
[13782.861751] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[13782.864430] sd 0:0:0:0: [sda] Starting disk
[13782.873153] Extended CMOS year: 2000
[13782.981401] PM: resume of drv:hub dev:3-0:1.0 complete after 119.546 msecs
[13782.981412] PM: resume of drv:hub dev:2-0:1.0 complete after 119.678 msecs
[13782.981429] PM: resume of drv: dev:ep_00 complete after 119.646 msecs
[13782.981444] PM: resume of drv: dev:ep_81 complete after 119.525 msecs
[13782.981452] PM: resume of drv: dev:ep_81 complete after 119.682 msecs
[13782.981467] PM: resume of drv: dev:ep_00 complete after 117.639 msecs
[13782.981485] PM: resume of drv:hub dev:4-0:1.0 complete after 117.691 msecs
[13782.981496] PM: resume of drv: dev:ep_00 complete after 119.575 msecs
[13782.981511] PM: resume of drv: dev:ep_81 complete after 117.706 msecs
[13782.981597] PM: resume of drv:hub dev:5-0:1.0 complete after 117.549 msecs
[13782.981625] PM: resume of drv: dev:ep_81 complete after 117.508 msecs
[13782.981641] PM: resume of drv: dev:ep_00 complete after 117.394 msecs
[13782.985343] PM: resume of drv: dev:ep_00 complete after 123.948 msecs
[13782.985363] PM: resume of drv:hub dev:1-0:1.0 complete after 128.622 msecs
[13782.985400] PM: resume of drv: dev:ep_81 complete after 124.023 msecs
[13783.050199] PM: resume of drv:r8169 dev:0000:01:00.0 complete after 193.737 msecs
[13783.065431] PM: resume of drv:rts_pstor dev:0000:03:00.0 complete after 208.902 msecs
[13783.065464] PM: resume of drv:scsi dev:host4 complete after 200.731 msecs
[13783.065494] PM: resume of drv:scsi_host dev:host4 complete after 200.702 msecs
[13783.065525] PM: resume of drv:scsi dev:target4:0:0 complete after 200.673 msecs
[13783.065561] PM: resume of drv:sd dev:4:0:0:0 complete after 200.647 msecs
[13783.065583] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 200.605 msecs
[13783.097283] usb 1-3: reset high-speed USB device number 2 using ehci_hcd
[13783.181196] ata2: SATA link down (SStatus 0 SControl 300)
[13783.340671] PM: resume of drv:uvcvideo dev:1-3:1.0 complete after 476.437 msecs
[13783.340680] PM: resume of drv: dev:ep_00 complete after 476.265 msecs
[13783.340716] PM: resume of drv:uvcvideo dev:1-3:1.1 complete after 476.360 msecs
[13783.340746] PM: resume of drv: dev:ep_82 complete after 476.449 msecs
[13785.199307] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[13785.204051] ata1.00: configured for UDMA/133
[13785.235524] PM: resume of drv:sd dev:0:0:0:0 complete after 2373.329 msecs
[13785.235558] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2373.233 msecs
[13785.235568] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2364.551 msecs
[13785.241231] PM: resume of devices complete after 2387.304 msecs
[13785.241487] PM: resume devices took 2.388 seconds
[13785.241562] PM: Finishing wakeup.
[13785.241566] Restarting tasks ... done.
[13791.380372] r8169 0000:01:00.0: eth0: link down
[13791.380980] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13791.439557] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13794.733061] wlan0: authenticate with 74:9d:dc:9a:c1:59 (try 1)
[13794.735076] wlan0: authenticated
[13794.752807] wlan0: associate with 74:9d:dc:9a:c1:59 (try 1)
[13794.755063] wlan0: RX AssocResp from 74:9d:dc:9a:c1:59 (capab=0x431 status=0 aid=3)
[13794.755075] wlan0: associated
[13794.756577] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13794.756897] cfg80211: Calling CRDA for country: US
[13796.108001] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[13796.108015] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108024] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[13796.108034] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108042] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[13796.108052] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108058] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[13796.108065] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108071] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[13796.108079] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108085] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[13796.108092] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108098] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[13796.108106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108112] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[13796.108119] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108125] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[13796.108132] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108139] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[13796.108146] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108152] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[13796.108159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108165] cfg80211: Disabling freq 2467 MHz
[13796.108169] cfg80211: Disabling freq 2472 MHz
[13796.108173] cfg80211: Disabling freq 2484 MHz
[13796.108183] cfg80211: Regulatory domain changed to country: US
[13796.108188] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13796.108195] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[13796.108202] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[13796.108208] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13796.108215] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13796.108221] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13796.108228] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[13805.404213] wlan0: no IPv6 routers present
```

---

### Post by userfriendly1992 on 2013-01-18
Output of lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b367 Chicony Electronics Co., Ltd
```

---

### Post by leef on 2013-01-18
Edit: post was wrong.

---

### Post by brusegadi on 2013-01-18
Since it works with cheese, there might be a way to make it work with skype.  Have you tried:

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)

EDIT: Also   [http://ubuntuforums.org/showthread.php?t=1482369](http://ubuntuforums.org/showthread.php?t=1482369)

---

