---
title: "VirtualBox... help me!"
date: 2007-07-29
forum: General Help
---

### Post by Archoniam on 2007-07-29
Okay, my VirtualBox is being weird. For some reason, my Ubuntu will not run my virtualbox correctly. It says i need to see /var/log/vbox-install.log and it says this:
```
cp: missing destination file operand after `/tmp/vbox.3/Module.symvers'
Try `cp --help' for more information.
Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.
```
I do not know how to specify that at all. I don't even know what the crap it's talking about.

Um, this is what the kernel specified when I was installing VirtualBox. [[IMG]http://img527.imageshack.us/img527/2398/screenshotrootclaptophosq4.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshotrootclaptophosq4.png)


Can anyone help?

[edit]
This is what my computer output when i ran "gmesh" or some crap like that XD
```
[   49.550708] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.550748] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   49.550769] sda: Write Protect is off
[   49.550775] sda: Mode Sense: 00 3a 00 00
[   49.550808] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.565687] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   49.589831] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   49.705673] input: PS/2 Mouse as /class/input/input8
[   49.710131] input: AlpsPS/2 ALPS GlidePoint as /class/input/input9
[   52.765999] ieee80211_crypt: registered algorithm 'NULL'
[   52.784803] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   52.785386] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   52.821689] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   52.822174] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   52.825686] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 18
[   52.826217] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.582511] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   53.228337] 8139too Fast Ethernet driver 0.9.28
[   53.228985] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 18
[   53.230788] eth1: RealTek RTL8139 at 0xe00e4400, 00:0a:e4:df:a4:5d, IRQ 18
[   53.230797] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   26.759677] eth1: link down
[   26.759728] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   54.376332] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.327827] input: Power Button (FF) as /class/input/input10
[   27.328008] ACPI: Power Button (FF) [PWRF]
[   27.328055] input: Lid Switch as /class/input/input11
[   27.328077] ACPI: Lid Switch [LID0]
[   27.328118] input: Sleep Button (CM) as /class/input/input12
[   27.330043] ACPI: Sleep Button (CM) [SLPB]
[   27.330090] input: Power Button (CM) as /class/input/input13
[   27.330848] ACPI: Power Button (CM) [PWB]
[   28.381183] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   28.394550] ACPI: Thermal Zone [THR0] (47 C)
[   28.399071] ACPI: Invalid passive threshold
[   28.401346] ACPI: Thermal Zone [THR1] (36 C)
[   28.502970] ACPI: AC Adapter [AC] (on-line)
[   28.536114] ACPI: Battery Slot [BAT0] (battery present)
[   30.743371] eth0: no IPv6 routers present
[ 1471.626203] ACPI: PCI interrupt for device 0000:06:05.0 disabled
[ 1103.762908] ieee80211_crypt: unregistered algorithm 'NULL'
[ 1472.298224] ACPI: PCI interrupt for device 0000:06:07.0 disabled
[  737.050485] PM: Preparing system for mem sleep
[  737.050493] Disabling non-boot CPUs ...
[  737.050495] Stopping tasks ... done.
[ 1474.132761] Suspending console(s)
[ 1474.132781] platform bluetooth: suspend
[ 1474.132798] ac97 0-0:AD1981B: suspend
[ 1474.132817] iTCO_wdt iTCO_wdt: suspend
[ 1474.132826] sr 0:0:1:0: suspend
[ 1474.132883] sd 0:0:0:0: suspend
[ 1474.266046]  usbdev5.1_ep81: PM: suspend 0->2, parent 5-0:1.0 already 2
[ 1474.266057] hub 5-0:1.0: PM: suspend 2-->2
[ 1474.266063] hub 5-0:1.0: PM: suspend 2->2, parent usb5 already 2
[ 1474.266070]  usbdev5.1_ep00: PM: suspend 0->2, parent usb5 already 2
[ 1474.266077] usb usb5: PM: suspend 2-->2
[ 1474.266084]  usbdev4.1_ep81: PM: suspend 0->2, parent 4-0:1.0 already 2
[ 1474.266090] hub 4-0:1.0: PM: suspend 2-->2
[ 1474.266097] hub 4-0:1.0: PM: suspend 2->2, parent usb4 already 2
[ 1474.266104]  usbdev4.1_ep00: PM: suspend 0->2, parent usb4 already 2
[ 1474.266111] usb usb4: PM: suspend 2-->2
[ 1474.266117]  usbdev3.1_ep81: PM: suspend 0->2, parent 3-0:1.0 already 2
[ 1474.266124] hub 3-0:1.0: PM: suspend 2-->2
[ 1474.266130] hub 3-0:1.0: PM: suspend 2->2, parent usb3 already 2
[ 1474.266138]  usbdev3.1_ep00: PM: suspend 0->2, parent usb3 already 2
[ 1474.266145] usb usb3: PM: suspend 2-->2
[ 1474.266151]  usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[ 1474.266158] hub 2-0:1.0: PM: suspend 2-->2
[ 1474.266163] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[ 1474.266171]  usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[ 1474.266178] usb usb2: PM: suspend 2-->2
[ 1474.266185]  usbdev1.1_ep81: PM: suspend 0->2, parent 1-0:1.0 already 2
[ 1474.266191] hub 1-0:1.0: PM: suspend 2-->2
[ 1474.266197] hub 1-0:1.0: PM: suspend 2->2, parent usb1 already 2
[ 1474.266204]  usbdev1.1_ep00: PM: suspend 0->2, parent usb1 already 2
[ 1474.266210] usb usb1: PM: suspend 2-->2
[ 1474.266216] platform vesafb.0: suspend
[ 1474.266227] platform eisa.0: suspend
[ 1474.266233] i8042 i8042: suspend
[ 1474.295664] serial8250 serial8250: suspend
[ 1474.296058] pci_express 0000:00:1c.0:pcie02: suspend
[ 1474.296064] pci_express 0000:00:1c.0:pcie00: suspend
[ 1474.296070] platform pcspkr: suspend
[ 1474.296082] i8042 aux 00:07: suspend
[ 1474.296088] i8042 kbd 00:06: suspend
[ 1474.296093] pnp 00:05: suspend
[ 1474.296098] system 00:04: suspend
[ 1474.296103] pnp 00:03: suspend
[ 1474.296108] pnp 00:02: suspend
[ 1474.296112] pnp 00:01: suspend
[ 1474.296117] pnp 00:00: suspend
[ 1474.296123] pci 0000:06:07.0: suspend
[ 1474.296219] sdhci 0000:06:06.4: suspend
[ 1474.296423] ACPI: PCI interrupt for device 0000:06:06.4 disabled
[ 1474.297056] tifm_7xx1 0000:06:06.3: suspend
[ 1474.297179] ACPI: PCI interrupt for device 0000:06:06.3 disabled
[ 1474.297803] ohci1394 0000:06:06.2: suspend
[ 1474.297810] ohci1394 does not fully support suspend and resume yet
[ 1474.297816] ieee1394: hpsb_bus_reset called while bus reset already in progress
[ 1474.298463] yenta_cardbus 0000:06:06.0: suspend
[ 1474.298620] pci 0000:06:05.0: suspend
[ 1474.298714] pci 0000:00:1f.3: suspend
[ 1474.298766] ata_piix 0000:00:1f.1: suspend
[ 1474.301048] ata2: ACPI get timing mode failed.
[ 1474.301102] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[ 1474.301109] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
[ 1474.301117] pci 0000:00:1f.0: suspend
[ 1474.301169] pci 0000:00:1e.3: suspend
[ 1474.301237] Intel ICH 0000:00:1e.2: suspend
[ 1474.301441] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
[ 1474.301507] pci 0000:00:1e.0: suspend
[ 1474.301573] ehci_hcd 0000:00:1d.7: suspend, may wakeup
[ 1474.301667] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 1474.302230] uhci_hcd 0000:00:1d.3: suspend
[ 1474.302282] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[ 1474.302290] uhci_hcd 0000:00:1d.2: suspend
[ 1474.302340] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[ 1474.302346] uhci_hcd 0000:00:1d.1: suspend
[ 1474.302396] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[ 1474.302402] uhci_hcd 0000:00:1d.0: suspend
[ 1474.302453] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[ 1474.302459] pcieport-driver 0000:00:1c.0: suspend
[ 1474.302560] pci 0000:00:02.1: suspend
[ 1474.302596] pci 0000:00:02.0: suspend
[ 1474.302633] agpgart-intel 0000:00:00.0: suspend
[ 1474.302670] acpi acpi: suspend
[ 1474.302686] PM: Entering mem sleep
[ 1474.302691] platform bluetooth: LATE suspend
[ 1474.302699] iTCO_wdt iTCO_wdt: LATE suspend
[ 1474.302706] platform vesafb.0: LATE suspend
[ 1474.302712] platform eisa.0: LATE suspend
[ 1474.302717] i8042 i8042: LATE suspend
[ 1474.302722] serial8250 serial8250: LATE suspend
[ 1474.302762] platform pcspkr: LATE suspend
[ 1474.302768] pci 0000:06:07.0: LATE suspend
[ 1474.302773] sdhci 0000:06:06.4: LATE suspend
[ 1474.302778] tifm_7xx1 0000:06:06.3: LATE suspend
[ 1474.302783] ohci1394 0000:06:06.2: LATE suspend
[ 1474.302788] yenta_cardbus 0000:06:06.0: LATE suspend
[ 1474.302793] pci 0000:06:05.0: LATE suspend
[ 1474.302798] pci 0000:00:1f.3: LATE suspend
[ 1474.302803] pci 0000:00:1f.0: LATE suspend
[ 1474.302808] pci 0000:00:1e.3: LATE suspend
[ 1474.302813] Intel ICH 0000:00:1e.2: LATE suspend
[ 1474.302818] pci 0000:00:1e.0: LATE suspend
[ 1474.302823] pcieport-driver 0000:00:1c.0: LATE suspend
[ 1474.302828] pci 0000:00:02.1: LATE suspend
[ 1474.302833] pci 0000:00:02.0: LATE suspend
[ 1474.302838] agpgart-intel 0000:00:00.0: LATE suspend
[ 1474.302991] lapic suspend on CPU#0
[ 1474.303017]  [<c01154ef>] lapic_suspend+0xef/0x140
[ 1474.303059]  [<c02612cc>] sysdev_suspend+0xec/0x290
[ 1474.303071]  [<c0266a50>] device_power_down+0x90/0x170
[ 1474.303148]  [<c014d6af>] suspend_enter+0x2f/0x80
[ 1474.303158]  [<c012898b>] printk+0x1b/0x20
[ 1474.303193]  [<c014d869>] enter_state+0x169/0x1f0
[ 1474.303239]  [<c014d9a1>] state_store+0xb1/0xc0
[ 1474.303263]  [<c014d8f0>] state_store+0x0/0xc0
[ 1474.303292]  [<c01c1019>] subsys_attr_store+0x29/0x40
[ 1474.303326]  [<c01c134c>] sysfs_write_file+0x8c/0xf0
[ 1474.303378]  [<c017f76e>] vfs_write+0xbe/0x190
[ 1474.303404]  [<c01c12c0>] sysfs_write_file+0x0/0xf0
[ 1474.303439]  [<c017ff01>] sys_write+0x41/0x70
[ 1474.303485]  [<c01033b0>] sysenter_past_esp+0x69/0xa9
[ 1474.303545]  [<c02f0033>] unix_bind+0x283/0x2c0
[ 1474.303601]  =======================
[    1.060649] Back to C!
[    1.061079] lapic resume on CPU#0
[    1.061139]  [<c011521d>] lapic_resume+0x4d/0x1e0
[    1.061260]  [<c0260d51>] __sysdev_resume+0x11/0x80
[    1.061317]  [<c02614ae>] sysdev_resume+0x3e/0x70
[    1.061368]  [<c0267025>] device_power_up+0x5/0x10
[    1.061380]  [<c014d6f2>] suspend_enter+0x72/0x80
[    1.061391]  [<c012898b>] printk+0x1b/0x20
[    1.061449]  [<c014d869>] enter_state+0x169/0x1f0
[    1.061521]  [<c014d9a1>] state_store+0xb1/0xc0
[    1.061559]  [<c014d8f0>] state_store+0x0/0xc0
[    1.061608]  [<c01c1019>] subsys_attr_store+0x29/0x40
[    1.061662]  [<c01c134c>] sysfs_write_file+0x8c/0xf0
[    1.061744]  [<c017f76e>] vfs_write+0xbe/0x190
[    1.061785]  [<c01c12c0>] sysfs_write_file+0x0/0xf0
[    1.061837]  [<c017ff01>] sys_write+0x41/0x70
[    1.061908]  [<c01033b0>] sysenter_past_esp+0x69/0xa9
[    1.062005]  [<c02f0033>] unix_bind+0x283/0x2c0
[    1.062092]  =======================
[    0.531344] agpgart-intel 0000:00:00.0: EARLY resume
[    0.531349] pci 0000:00:02.0: EARLY resume
[    0.531351] pci 0000:00:02.1: EARLY resume
[    0.531354] pcieport-driver 0000:00:1c.0: EARLY resume
[    0.531357] uhci_hcd 0000:00:1d.0: EARLY resume
[    0.531360] uhci_hcd 0000:00:1d.1: EARLY resume
[    0.531363] uhci_hcd 0000:00:1d.2: EARLY resume
[    0.531365] uhci_hcd 0000:00:1d.3: EARLY resume
[    0.531368] ehci_hcd 0000:00:1d.7: EARLY resume
[    0.531371] pci 0000:00:1e.0: EARLY resume
[    0.531374] Intel ICH 0000:00:1e.2: EARLY resume
[    0.531376] pci 0000:00:1e.3: EARLY resume
[    0.531379] pci 0000:00:1f.0: EARLY resume
[    0.531382] ata_piix 0000:00:1f.1: EARLY resume
[    0.531385] pci 0000:00:1f.3: EARLY resume
[    0.531387] pci 0000:06:05.0: EARLY resume
[    0.531390] yenta_cardbus 0000:06:06.0: EARLY resume
[    0.531397] ohci1394 0000:06:06.2: EARLY resume
[    0.531400] tifm_7xx1 0000:06:06.3: EARLY resume
[    0.531403] sdhci 0000:06:06.4: EARLY resume
[    0.531405] pci 0000:06:07.0: EARLY resume
[    0.531412] platform pcspkr: EARLY resume
[    0.531508] serial8250 serial8250: EARLY resume
[    0.531512] i8042 i8042: EARLY resume
[    0.531514] platform eisa.0: EARLY resume
[    0.531517] platform vesafb.0: EARLY resume
[    0.531527] iTCO_wdt iTCO_wdt: EARLY resume
[    0.531536] platform bluetooth: EARLY resume
[    0.531538] PM: Finishing wakeup.
[    0.531543] acpi acpi: resuming
[    0.533016] agpgart-intel 0000:00:00.0: resuming
[    0.533045] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10b)
[    0.553260] pci 0000:00:02.0: resuming
[    0.553386] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[    0.553392] pci 0000:00:02.1: resuming
[    0.553406] PM: Writing back config space on device 0000:00:02.1 at offset 4 (was 0, writing 34000000)
[    0.553419] pcieport-driver 0000:00:1c.0: resuming
[    0.553430] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 100, writing 4010a)
[    0.553444] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing 1fff1)
[    0.553457] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing fff0)
[    0.553464] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 0, writing 200000f0)
[    0.553471] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
[    0.553481] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810008)
[    0.553490] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100004)
[    0.553522] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.553529] uhci_hcd 0000:00:1d.0: resuming
[    0.553534] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    0.553541] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.553629] usb usb1: root hub lost power or was reset
[    0.553647] uhci_hcd 0000:00:1d.1: resuming
[    0.553652] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    0.553659] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.553710] usb usb2: root hub lost power or was reset
[    0.553727] uhci_hcd 0000:00:1d.2: resuming
[    0.553731] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    0.553738] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.553794] usb usb4: root hub lost power or was reset
[    0.553810] uhci_hcd 0000:00:1d.3: resuming
[    0.553815] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 22
[    0.553822] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    0.553874] usb usb5: root hub lost power or was reset
[    0.553890] ehci_hcd 0000:00:1d.7: resuming
[    0.554984] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    0.554996] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.555075] pci 0000:00:1e.0: resuming
[    0.555091] PM: Writing back config space on device 0000:00:1e.0 at offset f (was 40000, writing 400ff)
[    0.555111] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 33f13001)
[    0.555118] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing b010b010)
[    0.555130] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 22800010, writing 22803030)
[    0.555137] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 80070600, writing 800a0600)
[    0.555155] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100005, writing 100107)
[    0.555200] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.555205] Intel ICH 0000:00:1e.2: resuming
[    0.555221] PM: Writing back config space on device 0000:00:1e.2 at offset f (was 100, writing 10a)
[    0.555243] PM: Writing back config space on device 0000:00:1e.2 at offset 7 (was 0, writing b0040400)
[    0.555255] PM: Writing back config space on device 0000:00:1e.2 at offset 6 (was 0, writing b0040800)
[    0.555262] PM: Writing back config space on device 0000:00:1e.2 at offset 5 (was 1d01, writing 18c1)
[    0.555279] PM: Writing back config space on device 0000:00:1e.2 at offset 1 (was 2900005, writing 2900003)
[    0.555309] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
[    0.555318] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[    1.219472] pci 0000:00:1e.3: resuming
[    1.219488] PM: Writing back config space on device 0000:00:1e.3 at offset f (was 200, writing 20b)
[    1.219516] PM: Writing back config space on device 0000:00:1e.3 at offset 5 (was 1f01, writing 2001)
[    1.219528] PM: Writing back config space on device 0000:00:1e.3 at offset 4 (was 1e01, writing 2401)
[    1.219544] PM: Writing back config space on device 0000:00:1e.3 at offset 1 (was 2900005, writing 2900001)
[    1.219569] pci 0000:00:1f.0: resuming
[    1.219624] ata_piix 0000:00:1f.1: resuming
[    1.219636] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 1ff)
[    1.219671] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
[    1.219694] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[    1.219706] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    1.221304] ata2: ACPI set timing mode failed.
[    1.221335] pci 0000:00:1f.3: resuming
[    1.221383] pci 0000:06:05.0: resuming
[    1.221403] PM: Writing back config space on device 0000:06:05.0 at offset f (was 18030100, writing 1803010b)
[    1.221446] PM: Writing back config space on device 0000:06:05.0 at offset 4 (was 0, writing b0106000)
[    1.221459] PM: Writing back config space on device 0000:06:05.0 at offset 3 (was 0, writing 8008)
[    1.221475] PM: Writing back config space on device 0000:06:05.0 at offset 1 (was 2900000, writing 2900102)
[    1.221507] yenta_cardbus 0000:06:06.0: resuming
[    1.221527] PM: Writing back config space on device 0000:06:06.0 at offset f (was 3c001ff, writing 5c0010a)
[    1.221540] PM: Writing back config space on device 0000:06:06.0 at offset e (was 0, writing 38fc)
[    1.221558] PM: Writing back config space on device 0000:06:06.0 at offset d (was 0, writing 3800)
[    1.221570] PM: Writing back config space on device 0000:06:06.0 at offset c (was 0, writing 34fc)
[    1.221582] PM: Writing back config space on device 0000:06:06.0 at offset b (was 0, writing 3400)
[    1.221595] PM: Writing back config space on device 0000:06:06.0 at offset a (was 0, writing 3bfff000)
[    1.221608] PM: Writing back config space on device 0000:06:06.0 at offset 9 (was 0, writing 38000000)
[    1.221621] PM: Writing back config space on device 0000:06:06.0 at offset 8 (was 0, writing 33fff000)
[    1.221633] PM: Writing back config space on device 0000:06:06.0 at offset 7 (was 0, writing 30000000)
[    1.221646] PM: Writing back config space on device 0000:06:06.0 at offset 6 (was 0, writing b00a0706)
[    1.221661] PM: Writing back config space on device 0000:06:06.0 at offset 4 (was 0, writing b0107000)
[    1.221680] PM: Writing back config space on device 0000:06:06.0 at offset 3 (was 820010, writing 82a820)
[    1.221695] PM: Writing back config space on device 0000:06:06.0 at offset 1 (was 2100000, writing 2100007)
[    1.221963] ohci1394 0000:06:06.2: resuming
[    1.222008] ata2: port disabled. ignoring.
[    1.223182] PM: Writing back config space on device 0000:06:06.2 at offset f (was 4020300, writing 402030b)
[    1.223217] PM: Writing back config space on device 0000:06:06.2 at offset 5 (was 0, writing b0100000)
[    1.223230] PM: Writing back config space on device 0000:06:06.2 at offset 4 (was d0204000, writing b0108000)
[    1.223244] PM: Writing back config space on device 0000:06:06.2 at offset 3 (was 800000, writing 808008)
[    1.223259] PM: Writing back config space on device 0000:06:06.2 at offset 1 (was 2100010, writing 2100116)
[    0.654229] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[b0108000-b01087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.654260] tifm_7xx1 0000:06:06.3: resuming
[    0.654947] PM: Writing back config space on device 0000:06:06.3 at offset f (was 40701ff, writing 407010a)
[    0.654978] PM: Writing back config space on device 0000:06:06.3 at offset 4 (was 0, writing b0104000)
[    0.654987] PM: Writing back config space on device 0000:06:06.3 at offset 3 (was 800000, writing 808008)
[    0.654998] PM: Writing back config space on device 0000:06:06.3 at offset 1 (was 2100000, writing 2100106)
[    0.655027] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 22 (level, low) -> IRQ 17
[    0.655054] sdhci 0000:06:06.4: resuming
[    0.655722] PM: Writing back config space on device 0000:06:06.4 at offset f (was 40701ff, writing 407010a)
[    0.655748] PM: Writing back config space on device 0000:06:06.4 at offset 6 (was 0, writing b0108800)
[    0.655757] PM: Writing back config space on device 0000:06:06.4 at offset 5 (was 0, writing b0108c00)
[    0.655765] PM: Writing back config space on device 0000:06:06.4 at offset 4 (was 0, writing b0109000)
[    0.655773] PM: Writing back config space on device 0000:06:06.4 at offset 3 (was 800000, writing 808008)
[    0.655784] PM: Writing back config space on device 0000:06:06.4 at offset 1 (was 2100000, writing 2100106)
[    0.655812] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 22 (level, low) -> IRQ 17
[    1.315106] pci 0000:06:07.0: resuming
[    1.315148] PM: Writing back config space on device 0000:06:07.0 at offset 5 (was 9400, writing b0109400)
[    1.315175] PM: Writing back config space on device 0000:06:07.0 at offset 1 (was 2900107, writing 2900103)
[    1.315208] pnp 00:00: resuming
[    1.315213] pnp 00:01: resuming
[    1.315217] pnp 00:02: resuming
[    1.315221] pnp 00:03: resuming
[    1.315225] system 00:04: resuming
[    1.315230] pnp 00:05: resuming
[    1.315234] i8042 kbd 00:06: resuming
[    1.315239] pnp: Device 00:06 does not support activation.
[    1.315245] i8042 aux 00:07: resuming
[    1.315249] pnp: Device 00:07 does not support activation.
[    1.315262] platform pcspkr: resuming
[    1.315268] pci_express 0000:00:1c.0:pcie00: resuming
[    1.315273] pci_express 0000:00:1c.0:pcie02: resuming
[    1.315677] serial8250 serial8250: resuming
[    1.315689] i8042 i8042: resuming
[    1.320358] atkbd serio0: resuming
[    1.323543] platform eisa.0: resuming
[    1.323549] serio serio1: resuming
[    1.323557] serio serio2: resuming
[    1.323562] serio serio3: resuming
[    1.323567] psmouse serio4: resuming
[    1.327118] platform vesafb.0: resuming
[    1.327124] usb usb1: resuming
[    1.330107] usb usb2: resuming
[    1.332607]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
[    1.332615]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
[    1.332621] usb usb4: resuming
[    1.335222] usb usb5: resuming
[    1.337832] sd 0:0:0:0: resuming
[    1.337846] sr 0:0:1:0: resuming
[    1.337857] iTCO_wdt iTCO_wdt: resuming
[    1.337875] ac97 0-0:AD1981B: resuming
[    1.337889] platform bluetooth: resuming
[    1.341223] Restarting tasks ... done.
[    0.693611] Enabling non-boot CPUs ...
[    1.693499] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.719630] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.746654] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.761682] ata1.00: configured for UDMA/33
[    1.774373] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.788159] ata1.01: configured for MWDMA2
[    1.796512] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    1.800122] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.801621] sda: Write Protect is off
[    1.801630] sda: Mode Sense: 00 3a 00 00
[    1.808744] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.815712] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    1.815755] sda: Write Protect is off
[    1.815761] sda: Mode Sense: 00 3a 00 00
[    1.815796] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.052151] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    1.377433] ieee80211_crypt: registered algorithm 'NULL'
[    1.385302] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    1.385555] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    1.393592] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[    1.393854] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    1.394417] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 18
[    1.394662] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    1.579386] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[    1.605029] 8139too Fast Ethernet driver 0.9.28
[    1.605364] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 18
[    1.606515] eth1: RealTek RTL8139 at 0xe02e6400, 00:0a:e4:df:a4:5d, IRQ 18
[    1.606696] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[    1.685329] input: PS/2 Mouse as /class/input/input14
[    1.706066] input: AlpsPS/2 ALPS GlidePoint as /class/input/input15
[    1.794481] eth1: link down
[    1.794706] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    2.459279] input: Power Button (FF) as /class/input/input16
[    2.501802] ACPI: Power Button (FF) [PWRF]
[    2.569796] input: Lid Switch as /class/input/input17
[    2.608732] ACPI: Lid Switch [LID0]
[    2.658008] input: Sleep Button (CM) as /class/input/input18
[    2.658549] ACPI: Sleep Button (CM) [SLPB]
[    2.682017] input: Power Button (CM) as /class/input/input19
[    2.682522] ACPI: Power Button (CM) [PWB]
[    3.399518] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    3.411907] ACPI: Thermal Zone [THR0] (45 C)
[    3.414633] ACPI: Invalid passive threshold
[    3.415427] ACPI: Thermal Zone [THR1] (34 C)
[    3.490723] ACPI: AC Adapter [AC] (on-line)
[    3.538564] ACPI: Battery Slot [BAT0] (battery present)
[   14.440401] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.912743] eth0: no IPv6 routers present
root@claptop:/home/archoniam# 

```

---

### Post by Archoniam on 2007-07-29
Also, I have seen the guy who installed the kernel-header choke crap. Already got it, same problem.

(W00t 40th bean!)

---

