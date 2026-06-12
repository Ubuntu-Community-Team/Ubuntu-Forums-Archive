---
title: "two minutes to arrive on my desktop ! very fast !"
date: 2016-05-07
forum: General Help
---

### Post by valereguerin on 2016-05-07
sudo reboot now

wait......wait.....wait    again wait.....two minutes later howououou i see my desktop !

windows vista is more faster......

i7 930 blomfield / 8 giga ram .....

and now when i open firefox, again one or two minutes for launch a research, marvellous.....

i will try with windows 95......

and i have "preload package" installed  !  pffuuuuu my pentium 4 "1990" is more faster ! and it's the same thing on 14.04 ! LTS

i change my canal wifi reset my internet connection call my operator for test it, launch speed test adsl !

it's not my boxe !

---

### Post by ventrical on 2016-05-07
Pentium 4 1990!   Wha ????

More like 386DX 20Mhz

bwahahaha...

Did you try to install from normal ISO?

---

### Post by sudodus on 2016-05-07
If systemd is unhappy with something, there is a delay of 1 min 30 s. Maybe you are affected by it. Boot without the boot options 'quiet splash' and watch the text on the screen. Maybe it will show what is the problem.

---

### Post by PJs Ronin on 2016-05-07
When next you have a desktop, perhaps try:

```

systemd-analyze blame
```

to see where the culprit(s) lay.

---

### Post by valereguerin on 2016-05-08
```
 freeman@Sniper-one:~$ systemd-analyze blame
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
lines 1-2...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
lines 1-3...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
lines 1-4...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
lines 1-5...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
lines 1-6...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
lines 1-7...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
lines 1-8...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
lines 1-10...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
lines 1-11...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
lines 1-13...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
lines 1-14...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
lines 1-15...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
lines 1-16...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
lines 1-17...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
lines 1-18...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
          3.301s cpufreqd.service
lines 1-19...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
          3.301s cpufreqd.service
          3.249s virtualbox.service
lines 1-20...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
          3.301s cpufreqd.service
          3.249s virtualbox.service
          2.862s accounts-daemon.service
lines 1-21...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
          3.301s cpufreqd.service
          3.249s virtualbox.service
          2.862s accounts-daemon.service
          2.825s gpu-manager.service
          2.481s preload.service
lines 1-23...skipping...
         49.599s plymouth-quit-wait.service
         24.105s apt-cacher.service
         17.484s postgresql@9.5-main.service
         17.442s postgresql@9.4-main.service
         16.548s NetworkManager-wait-online.service
          9.762s postfix.service
          9.409s teamviewerd.service
          7.632s ntop.service
          6.826s ModemManager.service
          6.581s kdump-tools.service
          6.448s collectl.service
          5.828s apparmor.service
          5.126s ebtables.service
          4.624s dev-sdb3.device
          4.199s NetworkManager.service
          3.921s vboxweb.service
          3.737s samhain.service
          3.604s plymouth-read-write.service
          3.301s cpufreqd.service
          3.249s virtualbox.service
          2.862s accounts-daemon.service
          2.825s gpu-manager.service
          2.481s preload.service
          2.473s irqbalance.service
lines 1-24

```

---

### Post by valereguerin on 2016-05-08
i think it's again network-manager, it manage nothing, my connection up down up down up down all the time, 10 minutes for watch 5 minutes youtube video ! without proxy ! just one page open !  surf is HHARRRRGGGGGGGGG

---

### Post by valereguerin on 2016-05-08
```
# dmesg : [ 4490.440330] [drm:si_dpm_set_power_state [radeon]] *ERROR* si_restrict_performance_levels_before_switch failed

[   10.763443] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x000000000000042C-0x000000000000042D (\GP2C) (20160108/utaddress-255)

[    0.233827] ACPI: Added _OSI(Processor Aggregator Device)
[    0.352415] ACPI: Interpreter enabled
[    0.352429] ACPI: (supports S0 S3 S4 S5)
[    0.352430] ACPI: Using IOAPIC for interrupt routing
[    0.352448] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.355739] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.355744] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.355747] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.355905] PCI host bridge to bus 0000:00
[    0.355908] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.355909] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.355911] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.355912] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.355914] pci_bus 0000:00: root bus resource [mem 0xdff00000-0xfebfffff window]
[    0.355915] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.355925] pci 0000:00:00.0: [8086:3405] type 00 class 0x060000
[    0.355981] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.356048] pci 0000:00:01.0: [8086:3408] type 01 class 0x060400
[    0.356102] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.356166] pci 0000:00:02.0: [8086:3409] type 01 class 0x060400
[    0.356217] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.356281] pci 0000:00:03.0: [8086:340a] type 01 class 0x060400
[    0.356334] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.356403] pci 0000:00:10.0: [8086:3425] type 00 class 0x080000
[    0.356491] pci 0000:00:10.1: [8086:3426] type 00 class 0x080000
[    0.356575] pci 0000:00:11.0: [8086:3427] type 00 class 0x080000
[    0.356662] pci 0000:00:11.1: [8086:3428] type 00 class 0x080000
[    0.356747] pci 0000:00:13.0: [8086:342d] type 00 class 0x080020
[    0.356757] pci 0000:00:13.0: reg 0x10: [mem 0xfbfff000-0xfbffffff]
[    0.356801] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
[    0.356860] pci 0000:00:14.0: [8086:342e] type 00 class 0x080000
[    0.356954] pci 0000:00:14.1: [8086:3422] type 00 class 0x080000
[    0.357047] pci 0000:00:14.2: [8086:3423] type 00 class 0x080000
[    0.357141] pci 0000:00:15.0: [8086:342f] type 00 class 0x080020
[    0.357228] pci 0000:00:1a.0: [8086:3a37] type 00 class 0x0c0300
[    0.357265] pci 0000:00:1a.0: reg 0x20: [io  0xff00-0xff1f]
[    0.357328] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.357361] pci 0000:00:1a.1: [8086:3a38] type 00 class 0x0c0300
[    0.357399] pci 0000:00:1a.1: reg 0x20: [io  0xfe00-0xfe1f]
[    0.357462] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.357494] pci 0000:00:1a.2: [8086:3a39] type 00 class 0x0c0300
[    0.357531] pci 0000:00:1a.2: reg 0x20: [io  0xfd00-0xfd1f]
[    0.357593] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.357632] pci 0000:00:1a.7: [8086:3a3c] type 00 class 0x0c0320
[    0.357648] pci 0000:00:1a.7: reg 0x10: [mem 0xfbffe000-0xfbffe3ff]
[    0.357727] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.357760] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.357794] pci 0000:00:1c.0: [8086:3a40] type 01 class 0x060400
[    0.357854] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.357891] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.357923] pci 0000:00:1c.1: [8086:3a42] type 01 class 0x060400
[    0.357988] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.358025] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.358059] pci 0000:00:1c.3: [8086:3a46] type 01 class 0x060400
[    0.358123] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.358160] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.358192] pci 0000:00:1c.4: [8086:3a48] type 01 class 0x060400
[    0.358256] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.358296] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.358330] pci 0000:00:1d.0: [8086:3a34] type 00 class 0x0c0300
[    0.358368] pci 0000:00:1d.0: reg 0x20: [io  0xfc00-0xfc1f]
[    0.358430] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.358462] pci 0000:00:1d.1: [8086:3a35] type 00 class 0x0c0300
[    0.358500] pci 0000:00:1d.1: reg 0x20: [io  0xfb00-0xfb1f]
[    0.358561] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.358593] pci 0000:00:1d.2: [8086:3a36] type 00 class 0x0c0300
[    0.358631] pci 0000:00:1d.2: reg 0x20: [io  0xfa00-0xfa1f]
[    0.358694] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.358732] pci 0000:00:1d.7: [8086:3a3a] type 00 class 0x0c0320
[    0.358749] pci 0000:00:1d.7: reg 0x10: [mem 0xfbffd000-0xfbffd3ff]
[    0.358826] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.358860] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.358891] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.358962] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.358996] pci 0000:00:1f.0: [8086:3a16] type 00 class 0x060100
[    0.359068] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0400-0x047f]: address conflict with ACPI CPU throttle [io  0x0410-0x0415]
[    0.359072] pci 0000:00:1f.0: quirk: [io  0x0580-0x05bf] claimed by ICH6 GPIO
[    0.359075] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.359078] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.359159] pci 0000:00:1f.2: [8086:3a20] type 00 class 0x01018a
[    0.359171] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.359178] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.359185] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.359191] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.359198] pci 0000:00:1f.2: reg 0x20: [io  0xf900-0xf90f]
[    0.359205] pci 0000:00:1f.2: reg 0x24: [io  0xf800-0xf80f]
[    0.359214] pci 0000:00:1f.2: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.359215] pci 0000:00:1f.2: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.359216] pci 0000:00:1f.2: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.359218] pci 0000:00:1f.2: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.359293] pci 0000:00:1f.3: [8086:3a30] type 00 class 0x0c0500
[    0.359306] pci 0000:00:1f.3: reg 0x10: [mem 0xfbffc000-0xfbffc0ff 64bit]
[    0.359324] pci 0000:00:1f.3: reg 0x20: [io  0x0500-0x051f]
[    0.359398] pci 0000:00:1f.5: [8086:3a26] type 00 class 0x010185
[    0.359411] pci 0000:00:1f.5: reg 0x10: [io  0xf600-0xf607]
[    0.359418] pci 0000:00:1f.5: reg 0x14: [io  0xf500-0xf503]
[    0.359425] pci 0000:00:1f.5: reg 0x18: [io  0xf400-0xf407]
[    0.359431] pci 0000:00:1f.5: reg 0x1c: [io  0xf300-0xf303]
[    0.359439] pci 0000:00:1f.5: reg 0x20: [io  0xf200-0xf20f]
[    0.359445] pci 0000:00:1f.5: reg 0x24: [io  0xf100-0xf10f]
[    0.359565] pci 0000:01:00.0: [1b4b:918a] type 00 class 0x01018f
[    0.359576] pci 0000:01:00.0: reg 0x10: [io  0xef00-0xef07]
[    0.359583] pci 0000:01:00.0: reg 0x14: [io  0xee00-0xee03]
[    0.359589] pci 0000:01:00.0: reg 0x18: [io  0xed00-0xed07]
[    0.359598] pci 0000:01:00.0: reg 0x1c: [io  0xec00-0xec03]
[    0.359605] pci 0000:01:00.0: reg 0x20: [io  0xeb00-0xeb0f]
[    0.359611] pci 0000:01:00.0: reg 0x24: [mem 0xfb8ff000-0xfb8ff1ff]
[    0.359618] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.359650] pci 0000:01:00.0: PME# supported from D3hot
[    0.367647] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.367650] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.367653] pci 0000:00:01.0:   bridge window [mem 0xfb800000-0xfb8fffff]
[    0.367701] pci 0000:02:00.0: [1033:0194] type 00 class 0x0c0330
[    0.367718] pci 0000:02:00.0: reg 0x10: [mem 0xfbefe000-0xfbefffff 64bit]
[    0.367799] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.375689] pci 0000:00:02.0: PCI bridge to [bus 02]
[    0.375694] pci 0000:00:02.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.375738] pci 0000:03:00.0: [1002:679a] type 00 class 0x030000
[    0.375751] pci 0000:03:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.375759] pci 0000:03:00.0: reg 0x18: [mem 0xfba80000-0xfbabffff 64bit]
[    0.375765] pci 0000:03:00.0: reg 0x20: [io  0xbe00-0xbeff]
[    0.375776] pci 0000:03:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.375819] pci 0000:03:00.0: supports D1 D2
[    0.375820] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.375876] pci 0000:03:00.1: [1002:aaa0] type 00 class 0x040300
[    0.375889] pci 0000:03:00.1: reg 0x10: [mem 0xfbafc000-0xfbafffff 64bit]
[    0.375946] pci 0000:03:00.1: supports D1 D2
[    0.383730] pci 0000:00:03.0: PCI bridge to [bus 03]
[    0.383733] pci 0000:00:03.0:   bridge window [io  0xb000-0xbfff]
[    0.383735] pci 0000:00:03.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.383739] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.383778] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.383836] pci 0000:05:00.0: [1102:000b] type 00 class 0x040300
[    0.383863] pci 0000:05:00.0: reg 0x10: [mem 0xf9ff0000-0xf9ffffff 64bit]
[    0.383881] pci 0000:05:00.0: reg 0x18: [mem 0xf9c00000-0xf9dfffff 64bit]
[    0.383899] pci 0000:05:00.0: reg 0x20: [mem 0xf8000000-0xf8ffffff 64bit]
[    0.391775] pci 0000:00:1c.1: PCI bridge to [bus 05]
[    0.391780] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.391850] pci 0000:06:00.0: [197b:2363] type 00 class 0x010185
[    0.391937] pci 0000:06:00.0: reg 0x24: [mem 0xfbdfe000-0xfbdfffff]
[    0.392002] pci 0000:06:00.0: PME# supported from D3hot
[    0.392061] pci 0000:06:00.1: [197b:2363] type 00 class 0x010185
[    0.392080] pci 0000:06:00.1: reg 0x10: [io  0xdf00-0xdf07]
[    0.392089] pci 0000:06:00.1: reg 0x14: [io  0xde00-0xde03]
[    0.392098] pci 0000:06:00.1: reg 0x18: [io  0xdd00-0xdd07]
[    0.392108] pci 0000:06:00.1: reg 0x1c: [io  0xdc00-0xdc03]
[    0.392117] pci 0000:06:00.1: reg 0x20: [io  0xdb00-0xdb0f]
[    0.392215] pci 0000:06:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.392224] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.392227] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.392230] pci 0000:00:1c.3:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.392283] pci 0000:07:00.0: [1957:c006] type 00 class 0x0b2000
[    0.392301] pci 0000:07:00.0: reg 0x10: [mem 0xfbb00000-0xfbbfffff]
[    0.392312] pci 0000:07:00.0: reg 0x14: [mem 0xfbce0000-0xfbceffff]
[    0.392329] pci 0000:07:00.0: reg 0x18: [mem 0xfa000000-0xfaffffff 64bit pref]
[    0.392345] pci 0000:07:00.0: reg 0x20: [mem 0xfbcfc000-0xfbcfffff 64bit]
[    0.392421] pci 0000:07:00.0: supports D1 D2
[    0.392422] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot
[    0.392473] pci 0000:07:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.392480] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.392485] pci 0000:00:1c.4:   bridge window [mem 0xfbb00000-0xfbcfffff]
[    0.392490] pci 0000:00:1c.4:   bridge window [mem 0xfa000000-0xfaffffff 64bit pref]
[    0.392523] pci 0000:08:00.0: [1186:4300] type 00 class 0x020000
[    0.392538] pci 0000:08:00.0: reg 0x10: [io  0xce00-0xceff]
[    0.392546] pci 0000:08:00.0: reg 0x14: [mem 0xfb9ff000-0xfb9ff0ff]
[    0.392585] pci 0000:08:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.392612] pci 0000:08:00.0: supports D1 D2
[    0.392613] pci 0000:08:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.392679] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.392682] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.392685] pci 0000:00:1e.0:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.392690] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.392692] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.392693] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.392694] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.392696] pci 0000:00:1e.0:   bridge window [mem 0xdff00000-0xfebfffff window] (subtractive decode)
[    0.393086] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.393130] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.393172] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.393213] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.393255] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.393298] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.393341] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.393384] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.393538] vgaarb: setting as boot device: PCI:0000:03:00.0
[    0.393540] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.393542] vgaarb: loaded
[    0.393543] vgaarb: bridge control possible 0000:03:00.0
[    0.393722] SCSI subsystem initialized
[    0.393757] libata version 3.00 loaded.
[    0.393775] ACPI: bus type USB registered
[    0.393790] usbcore: registered new interface driver usbfs
[    0.393797] usbcore: registered new interface driver hub
[    0.393816] usbcore: registered new device driver usb
[    0.393929] PCI: Using ACPI for IRQ routing
[    0.395158] PCI: Discovered peer bus 3f
[    0.395159] PCI: root bus 3f: using default resources
[    0.395162] PCI: Probing PCI hardware (bus 3f)
[    0.395186] ACPI: \: failed to evaluate _DSM (0x1001)
[    0.395186] PCI host bridge to bus 0000:3f
[    0.395188] pci_bus 0000:3f: root bus resource [io  0x0000-0xffff]
[    0.395190] pci_bus 0000:3f: root bus resource [mem 0x00000000-0xfffffffff]
[    0.395191] pci_bus 0000:3f: No busn resource found for root bus, will use [bus 3f-ff]
[    0.395193] pci_bus 0000:3f: busn_res: can not insert [bus 3f-ff] under domain [bus 00-ff] (conflicts with (null) [bus 00-3f])
[    0.395198] pci 0000:3f:00.0: [8086:2c41] type 00 class 0x060000
[    0.395235] pci 0000:3f:00.1: [8086:2c01] type 00 class 0x060000
[    0.395272] pci 0000:3f:02.0: [8086:2c10] type 00 class 0x060000
[    0.395307] pci 0000:3f:02.1: [8086:2c11] type 00 class 0x060000
[    0.395343] pci 0000:3f:03.0: [8086:2c18] type 00 class 0x060000
[    0.395377] pci 0000:3f:03.1: [8086:2c19] type 00 class 0x060000
[    0.395412] pci 0000:3f:03.4: [8086:2c1c] type 00 class 0x060000
[    0.395448] pci 0000:3f:04.0: [8086:2c20] type 00 class 0x060000
[    0.395482] pci 0000:3f:04.1: [8086:2c21] type 00 class 0x060000
[    0.395517] pci 0000:3f:04.2: [8086:2c22] type 00 class 0x060000
[    0.395551] pci 0000:3f:04.3: [8086:2c23] type 00 class 0x060000
[    0.395589] pci 0000:3f:05.0: [8086:2c28] type 00 class 0x060000
[    0.395625] pci 0000:3f:05.1: [8086:2c29] type 00 class 0x060000
[    0.395659] pci 0000:3f:05.2: [8086:2c2a] type 00 class 0x060000
[    0.395694] pci 0000:3f:05.3: [8086:2c2b] type 00 class 0x060000
[    0.395730] pci 0000:3f:06.0: [8086:2c30] type 00 class 0x060000
[    0.395764] pci 0000:3f:06.1: [8086:2c31] type 00 class 0x060000
[    0.395802] pci 0000:3f:06.2: [8086:2c32] type 00 class 0x060000
[    0.395837] pci 0000:3f:06.3: [8086:2c33] type 00 class 0x060000
[    0.395881] pci_bus 0000:3f: busn_res: [bus 3f-ff] end is updated to 3f
[    0.395883] pci_bus 0000:3f: busn_res: can not insert [bus 3f] under domain [bus 00-ff] (conflicts with (null) [bus 00-3f])
[    0.395888] PCI: pci_cache_line_size set to 64 bytes
[    0.395978] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.395980] e820: reserve RAM buffer [mem 0xdfed0000-0xdfffffff]
[    0.396073] NetLabel: Initializing
[    0.396074] NetLabel:  domain hash size = 128
[    0.396075] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.396085] NetLabel:  unlabeled traffic allowed by default
[    0.396188] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.396192] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.396195] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.398380] clocksource: Switched to clocksource hpet
[    0.403773] VFS: Disk quotas dquot_6.6.0
[    0.403795] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.403874] AppArmor: AppArmor Filesystem Enabled
[    0.403929] pnp: PnP ACPI init
[    0.404083] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.404085] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.404087] system 00:00: [io  0x0800-0x087f] has been reserved
[    0.404089] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.404090] system 00:00: [io  0x0880-0x088f] has been reserved
[    0.404094] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.404152] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.404285] system 00:02: [io  0x0400-0x047f] could not be reserved
[    0.404287] system 00:02: [io  0x0580-0x05ff] could not be reserved
[    0.404290] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.404452] system 00:03: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.404455] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.404587] system 00:04: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.404589] system 00:04: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.404591] system 00:04: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.404592] system 00:04: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.404594] system 00:04: [mem 0xdfed0000-0xdfedffff] could not be reserved
[    0.404595] system 00:04: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.404597] system 00:04: [mem 0x00100000-0xdfecffff] could not be reserved
[    0.404599] system 00:04: [mem 0xdfee0000-0xdfefffff] has been reserved
[    0.404600] system 00:04: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.404602] system 00:04: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.404604] system 00:04: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.404605] system 00:04: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.404607] system 00:04: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.404608] system 00:04: [mem 0xfff00000-0xffffffff] has been reserved
[    0.404610] system 00:04: [mem 0x000e0000-0x000effff] has been reserved
[    0.404612] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.404616] pnp: PnP ACPI: found 5 devices
[    0.410624] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.410652] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.410654] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.410656] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000 add_align 100000
[    0.410662] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.410664] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000 add_align 100000
[    0.410671] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000 add_align 100000
[    0.410678] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000
[    0.410694] pci 0000:00:1f.0: BAR 13: [io  size 0x0080] has bogus alignment
[    0.410699] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.410701] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.410702] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410704] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410706] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410707] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410709] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410711] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.410712] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410714] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410715] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410717] pci 0000:00:1c.1: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410718] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410720] pci 0000:00:1c.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.410724] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
[    0.410728] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.410731] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.410734] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.410736] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.410738] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.410740] pci 0000:00:1c.4: BAR 13: assigned [io  0x3000-0x3fff]
[    0.410743] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb800000-0xfb80ffff pref]
[    0.410745] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.410748] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.410751] pci 0000:00:01.0:   bridge window [mem 0xfb800000-0xfb8fffff]
[    0.410756] pci 0000:00:02.0: PCI bridge to [bus 02]
[    0.410760] pci 0000:00:02.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.410766] pci 0000:03:00.0: BAR 6: assigned [mem 0xfba00000-0xfba1ffff pref]
[    0.410767] pci 0000:00:03.0: PCI bridge to [bus 03]
[    0.410769] pci 0000:00:03.0:   bridge window [io  0xb000-0xbfff]
[    0.410772] pci 0000:00:03.0:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.410775] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.410779] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.410781] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.410785] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.410788] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.410793] pci 0000:00:1c.1: PCI bridge to [bus 05]
[    0.410795] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.410798] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.410801] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.410806] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.410808] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.410812] pci 0000:00:1c.3:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.410815] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.410819] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.410821] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.410825] pci 0000:00:1c.4:   bridge window [mem 0xfbb00000-0xfbcfffff]
[    0.410828] pci 0000:00:1c.4:   bridge window [mem 0xfa000000-0xfaffffff 64bit pref]
[    0.410833] pci 0000:08:00.0: BAR 6: assigned [mem 0xfb900000-0xfb91ffff pref]
[    0.410835] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    0.410837] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.410840] pci 0000:00:1e.0:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.410847] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.410849] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.410850] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.410852] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.410853] pci_bus 0000:00: resource 8 [mem 0xdff00000-0xfebfffff window]
[    0.410855] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.410856] pci_bus 0000:01: resource 1 [mem 0xfb800000-0xfb8fffff]
[    0.410857] pci_bus 0000:02: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.410859] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.410860] pci_bus 0000:03: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.410862] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.410863] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.410865] pci_bus 0000:04: resource 1 [mem 0xf0000000-0xf01fffff]
[    0.410866] pci_bus 0000:04: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.410867] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.410869] pci_bus 0000:05: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.410870] pci_bus 0000:05: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.410871] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    0.410873] pci_bus 0000:06: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.410874] pci_bus 0000:06: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.410875] pci_bus 0000:07: resource 0 [io  0x3000-0x3fff]
[    0.410877] pci_bus 0000:07: resource 1 [mem 0xfbb00000-0xfbcfffff]
[    0.410878] pci_bus 0000:07: resource 2 [mem 0xfa000000-0xfaffffff 64bit pref]
[    0.410879] pci_bus 0000:08: resource 0 [io  0xc000-0xcfff]
[    0.410881] pci_bus 0000:08: resource 1 [mem 0xfb900000-0xfb9fffff]
[    0.410882] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7 window]
[    0.410884] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff window]
[    0.410885] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.410886] pci_bus 0000:08: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.410888] pci_bus 0000:08: resource 8 [mem 0xdff00000-0xfebfffff window]
[    0.410891] pci_bus 0000:3f: resource 4 [io  0x0000-0xffff]
[    0.410893] pci_bus 0000:3f: resource 5 [mem 0x00000000-0xfffffffff]
[    0.410919] NET: Registered protocol family 2
[    0.411085] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.411228] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.411392] TCP: Hash tables configured (established 65536 bind 65536)
[    0.411422] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.411452] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.411527] NET: Registered protocol family 1
[    0.442665] pci 0000:03:00.0: Video device with shadowed ROM
[    0.442672] pci 0000:06:00.0: async suspend disabled to avoid multi-function power-on ordering issue
[    0.442675] pci 0000:06:00.1: async suspend disabled to avoid multi-function power-on ordering issue
[    0.442699] PCI: CLS 64 bytes, default 64
[    0.442742] Trying to unpack rootfs image as initramfs...
[    0.933070] Freeing initrd memory: 33940K (ffff880033da6000 - ffff880035ecb000)
[    0.933121] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.933123] software IO TLB [mem 0xdbed0000-0xdfed0000] (64MB) mapped at [ffff8800dbed0000-ffff8800dfecffff]
[    0.933366] Scanning for low memory corruption every 60 seconds
[    0.933825] futex hash table entries: 4096 (order: 6, 262144 bytes)
[    0.933883] audit: initializing netlink subsys (disabled)
[    0.933899] audit: type=2000 audit(1462688123.708:1): initialized
[    0.934153] Initialise system trusted keyring
[    0.935640] zbud: loaded
[    0.936142] fuse init (API version 7.24)
[    0.936260] Key type big_key registered
[    0.936566] Key type asymmetric registered
[    0.936569] Asymmetric key parser 'x509' registered
[    0.936607] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.936638] io scheduler noop registered
[    0.936640] io scheduler deadline registered (default)
[    0.936668] io scheduler cfq registered
[    0.937012] pcieport 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.937144] pcieport 0000:00:1c.1: enabling device (0006 -> 0007)
[    0.937388] pcieport 0000:00:1c.4: enabling device (0006 -> 0007)
[    0.937522] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.937527] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.937556] intel_idle: MWAIT substates: 0x1120
[    0.937566] intel_idle: v0.4 model 0x1A
[    0.937567] intel_idle: lapic_timer_reliable_states 0x2
[    0.937868] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.937872] ACPI: Power Button [PWRB]
[    0.937919] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.937921] ACPI: Power Button [PWRF]
[    0.939198] GHES: HEST is not enabled!
[    0.939298] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.940874] Linux agpgart interface v0.103
[    0.944282] brd: module loaded
[    0.945646] loop: module loaded
[    0.945762] ata_piix 0000:00:1f.2: version 2.13
[    0.945835] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.946459] scsi host0: ata_piix
[    0.946676] scsi host1: ata_piix
[    0.946718] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    0.946722] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    0.946803] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.947470] scsi host2: ata_piix
[    0.947698] scsi host3: ata_piix
[    0.947736] ata3: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf200 irq 19
[    0.947739] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf300 bmdma 0xf208 irq 19
[    0.947825] libphy: Fixed MDIO Bus: probed
[    0.947828] tun: Universal TUN/TAP device driver, 1.6
[    0.947829] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.947878] PPP generic driver version 2.4.2
[    0.947943] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.947948] ehci-pci: EHCI PCI platform driver
[    0.948045] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.948051] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.948062] ehci-pci 0000:00:1a.7: debug port 1
[    0.951974] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.951982] ehci-pci 0000:00:1a.7: irq 18, io mem 0xfbffe000
[    0.962631] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.962684] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.962687] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.962693] usb usb1: Product: EHCI Host Controller
[    0.962695] usb usb1: Manufacturer: Linux 4.5.0-040500rc7-generic ehci_hcd
[    0.962696] usb usb1: SerialNumber: 0000:00:1a.7
[    0.962820] hub 1-0:1.0: USB hub found
[    0.962830] hub 1-0:1.0: 6 ports detected
[    0.963052] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.963056] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.963066] ehci-pci 0000:00:1d.7: debug port 1
[    0.966957] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.966966] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfbffd000
[    0.978486] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.978581] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.978583] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.978584] usb usb2: Product: EHCI Host Controller
[    0.978586] usb usb2: Manufacturer: Linux 4.5.0-040500rc7-generic ehci_hcd
[    0.978587] usb usb2: SerialNumber: 0000:00:1d.7
[    0.978708] hub 2-0:1.0: USB hub found
[    0.978716] hub 2-0:1.0: 6 ports detected
[    0.978877] ehci-platform: EHCI generic platform driver
[    0.978885] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.978889] ohci-pci: OHCI PCI platform driver
[    0.978899] ohci-platform: OHCI generic platform driver
[    0.978905] uhci_hcd: USB Universal Host Controller Interface driver
[    0.978984] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.978989] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.978994] uhci_hcd 0000:00:1a.0: detected 2 ports
[    0.979016] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    0.979047] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.979049] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.979050] usb usb3: Product: UHCI Host Controller
[    0.979052] usb usb3: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.979053] usb usb3: SerialNumber: 0000:00:1a.0
[    0.979169] hub 3-0:1.0: USB hub found
[    0.979180] hub 3-0:1.0: 2 ports detected
[    0.979362] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.979367] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.979373] uhci_hcd 0000:00:1a.1: detected 2 ports
[    0.979394] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    0.979425] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.979427] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.979428] usb usb4: Product: UHCI Host Controller
[    0.979430] usb usb4: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.979431] usb usb4: SerialNumber: 0000:00:1a.1
[    0.979547] hub 4-0:1.0: USB hub found
[    0.979555] hub 4-0:1.0: 2 ports detected
[    0.979731] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.979736] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.979741] uhci_hcd 0000:00:1a.2: detected 2 ports
[    0.979757] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    0.979790] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.979792] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.979793] usb usb5: Product: UHCI Host Controller
[    0.979795] usb usb5: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.979796] usb usb5: SerialNumber: 0000:00:1a.2
[    0.979915] hub 5-0:1.0: USB hub found
[    0.979923] hub 5-0:1.0: 2 ports detected
[    0.980101] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.980105] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.980111] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.980127] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    0.980160] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.980162] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.980163] usb usb6: Product: UHCI Host Controller
[    0.980165] usb usb6: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.980166] usb usb6: SerialNumber: 0000:00:1d.0
[    0.980285] hub 6-0:1.0: USB hub found
[    0.980293] hub 6-0:1.0: 2 ports detected
[    0.980472] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.980477] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.980482] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.980498] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    0.980530] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.980532] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.980533] usb usb7: Product: UHCI Host Controller
[    0.980534] usb usb7: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.980536] usb usb7: SerialNumber: 0000:00:1d.1
[    0.980651] hub 7-0:1.0: USB hub found
[    0.980660] hub 7-0:1.0: 2 ports detected
[    0.980837] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.980841] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.980846] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.980863] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    0.980896] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.980898] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.980899] usb usb8: Product: UHCI Host Controller
[    0.980901] usb usb8: Manufacturer: Linux 4.5.0-040500rc7-generic uhci_hcd
[    0.980902] usb usb8: SerialNumber: 0000:00:1d.2
[    0.980984] hub 8-0:1.0: USB hub found
[    0.980988] hub 8-0:1.0: 2 ports detected
[    0.981143] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    0.981147] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.086034] xhci_hcd 0000:02:00.0: hcc params 0x014042cb hci version 0x96 quirks 0x00000004
[    1.086166] usb usb9: New USB device found, idVendor=1d6b, idProduct=0002
[    1.086168] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.086170] usb usb9: Product: xHCI Host Controller
[    1.086171] usb usb9: Manufacturer: Linux 4.5.0-040500rc7-generic xhci-hcd
[    1.086172] usb usb9: SerialNumber: 0000:02:00.0
[    1.086264] hub 9-0:1.0: USB hub found
[    1.086271] hub 9-0:1.0: 2 ports detected
[    1.086338] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.086341] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 10
[    1.089492] usb usb10: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.089505] usb usb10: New USB device found, idVendor=1d6b, idProduct=0003
[    1.089506] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.089507] usb usb10: Product: xHCI Host Controller
[    1.089509] usb usb10: Manufacturer: Linux 4.5.0-040500rc7-generic xhci-hcd
[    1.089510] usb usb10: SerialNumber: 0000:02:00.0
[    1.089602] hub 10-0:1.0: USB hub found
[    1.089611] hub 10-0:1.0: 2 ports detected
[    1.089713] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.122760] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.122761] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.278437] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.374548] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.374857] mousedev: PS/2 mouse device common for all mice
[    1.375413] rtc_cmos 00:01: RTC can wake from S4
[    1.375677] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.375707] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.375722] i2c /dev entries driver
[    1.375800] device-mapper: uevent: version 1.0.3
[    1.375917] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.375934] ledtrig-cpu: registered to indicate activity on CPUs
[    1.376515] NET: Registered protocol family 10
[    1.376844] NET: Registered protocol family 17
[    1.376861] Key type dns_resolver registered
[    1.377425] microcode: CPU0 sig=0x106a5, pf=0x2, revision=0x19
[    1.377454] microcode: CPU1 sig=0x106a5, pf=0x2, revision=0x19
[    1.377497] microcode: CPU2 sig=0x106a5, pf=0x2, revision=0x19
[    1.377501] microcode: CPU3 sig=0x106a5, pf=0x2, revision=0x19
[    1.377528] microcode: CPU4 sig=0x106a5, pf=0x2, revision=0x19
[    1.377579] microcode: CPU5 sig=0x106a5, pf=0x2, revision=0x19
[    1.377604] microcode: CPU6 sig=0x106a5, pf=0x2, revision=0x19
[    1.377613] microcode: CPU7 sig=0x106a5, pf=0x2, revision=0x19
[    1.377656] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.378015] registered taskstats version 1
[    1.378039] Loading compiled-in X.509 certificates
[    1.379004] Loaded X.509 cert 'Build time autogenerated kernel key: c33d85a3b9a5d64f93a431bfa70f4ec6a0e0ce91'
[    1.379023] zswap: loaded using pool lzo/zbud
[    1.381237] Key type trusted registered
[    1.385554] Key type encrypted registered
[    1.385564] AppArmor: AppArmor sha1 policy hashing enabled
[    1.385569] ima: No TPM chip found, activating TPM-bypass!
[    1.385604] evm: HMAC attrs: 0x1
[    1.386220]   Magic number: 0:946:265
[    1.386402] rtc_cmos 00:01: setting system clock to 2016-05-08 06:15:24 UTC (1462688124)
[    1.387942] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.387945] EDD information not available.
[    1.387995] PM: Hibernation image not present or could not be loaded.
[    1.400513] usb 10-1: new SuperSpeed USB device number 2 using xhci_hcd
[    1.406625] usb 2-6: new high-speed USB device number 4 using ehci-pci
[    1.410656] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.414608] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.417199] ata3.00: ATA-10: WDC WD10EZEX-00WN4A0, 01.01A01, max UDMA/133
[    1.417203] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.419784] usb 1-1: New USB device found, idVendor=2109, idProduct=3431
[    1.419790] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.419792] usb 1-1: Product: USB2.0 Hub
[    1.420073] ata3.00: configured for UDMA/133
[    1.420188] hub 1-1:1.0: USB hub found
[    1.420411] hub 1-1:1.0: 4 ports detected
[    1.422511] usb 6-2: new low-speed USB device number 2 using uhci_hcd
[    1.427271] ata4.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    1.427276] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.443316] ata4.00: configured for UDMA/133
[    1.486358] usb 7-2: new low-speed USB device number 2 using uhci_hcd
[    1.538398] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.541252] usb 2-6: New USB device found, idVendor=0bda, idProduct=8172
[    1.541257] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.541260] usb 2-6: Product: RTL8191S WLAN Adapter 
[    1.541262] usb 2-6: Manufacturer: Manufacturer Realtek 
[    1.541265] usb 2-6: SerialNumber: 00e04c000001
[    1.577888] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.577901] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.590554] usb 6-2: New USB device found, idVendor=192f, idProduct=0416
[    1.590558] usb 6-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.590561] usb 6-2: Product: USB Optical Mouse
[    1.671683] usb 1-2: New USB device found, idVendor=2109, idProduct=3431
[    1.671688] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.671691] usb 1-2: Product: USB2.0 Hub
[    1.672074] hub 1-2:1.0: USB hub found
[    1.672277] hub 1-2:1.0: 4 ports detected
[    1.693477] usb 7-2: New USB device found, idVendor=413c, idProduct=2105
[    1.693482] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.693484] usb 7-2: Product: Dell USB Keyboard
[    1.693487] usb 7-2: Manufacturer: Dell
[    1.703387] usb 10-1: New USB device found, idVendor=2109, idProduct=0810
[    1.703392] usb 10-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.703394] usb 10-1: Product: 4-Port USB 3.0 Hub
[    1.703397] usb 10-1: Manufacturer: VIA Labs, Inc.
[    1.706555] hub 10-1:1.0: USB hub found
[    1.730520] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.730531] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.733038] ata2.00: ATA-8: ST9750420AS, 0003HPM1, max UDMA/133
[    1.733042] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.737853] ata2.00: configured for UDMA/133
[    1.738343] scsi 1:0:0:0: Direct-Access     ATA      ST9750420AS      HPM1 PQ: 0 ANSI: 5
[    1.758471] hub 10-1:1.0: 4 ports detected
[    1.762740] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.762838] sd 1:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/699 GiB)
[    1.762841] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.763043] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EZEX-00W 1A01 PQ: 0 ANSI: 5
[    1.763103] sd 1:0:0:0: [sda] Write Protect is off
[    1.763109] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.763267] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.786820] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.786843] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    1.786847] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    1.787160] sd 2:0:0:0: [sdb] Write Protect is off
[    1.787165] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.787247] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.787355] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
[    1.796922]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.798202] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.806685] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.806764] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    1.807130] sd 3:0:0:0: [sdc] Write Protect is off
[    1.807136] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.807249] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.862343]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[    1.863523] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.870046]  sdc: sdc1 sdc2 < sdc5 sdc6 sdc7 > sdc3
[    1.871055] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.872529] Freeing unused kernel memory: 1488K (ffffffff81f46000 - ffffffff820ba000)
[    1.872531] Write protecting the kernel read-only data: 14336k
[    1.873645] Freeing unused kernel memory: 1876K (ffff88000182b000 - ffff880001a00000)
[    1.873978] Freeing unused kernel memory: 48K (ffff880001df4000 - ffff880001e00000)
[    1.886675] random: systemd-udevd urandom read with 42 bits of entropy available
[    1.891403] usb 10-2: new SuperSpeed USB device number 3 using xhci_hcd
[    1.915309] wmi: Mapper loaded
[    1.915475] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.920712] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
[    1.928958] [drm] Initialized drm 1.1.0 20060810
[    1.929260] hidraw: raw HID events driver (C) Jiri Kosina
[    1.930349] tsc: Refined TSC clocksource calibration: 2798.011 MHz
[    1.930352] scsi host4: pata_jmicron
[    1.930355] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2854e9eaae1, max_idle_ns: 440795264633 ns
[    1.931733] scsi host5: pata_jmicron
[    1.931778] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 16
[    1.931780] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 16
[    1.931807] ahci 0000:06:00.0: version 3.0
[    1.935112] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.935190] r8169 0000:08:00.0 (unnamed net_device) (uninitialized): not PCI Express
[    1.935482] r8169 0000:08:00.0 eth0: RTL8169sb/8110sb at 0xffffc90000e88000, 6c:19:8f:99:82:bb, XID 10000000 IRQ 16
[    1.935485] r8169 0000:08:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    1.942020] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.942024] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.942413] scsi host6: ahci
[    1.942542] scsi host7: ahci
[    1.942603] ata7: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 19
[    1.942607] ata8: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 19
[    1.961703] [drm] radeon kernel modesetting enabled.
[    1.962522] r8169 0000:08:00.0 enp8s0: renamed from eth0
[    1.963956] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.963957] AMD IOMMUv2 functionality not available on this system
[    1.966721] CRAT table not found
[    1.966723] Finished initializing topology ret=0
[    1.966770] kfd kfd: Initialized module
[    1.967223] [drm] initializing kernel modesetting (TAHITI 0x1002:0x679A 0x174B:0xA003).
[    1.967236] [drm] register mmio base: 0xFBA80000
[    1.967237] [drm] register mmio size: 262144
[    1.967281] ATOM BIOS: R9
[    1.967342] [drm] Changing default dispclk from 500Mhz to 600Mhz
[    1.967353] radeon 0000:03:00.0: VRAM: 3072M 0x0000000000000000 - 0x00000000BFFFFFFF (3072M used)
[    1.967355] radeon 0000:03:00.0: GTT: 2048M 0x00000000C0000000 - 0x000000013FFFFFFF
[    1.967357] [drm] Detected VRAM RAM=3072M, BAR=256M
[    1.967358] [drm] RAM width 384bits DDR
[    1.967399] [TTM] Zone  kernel: Available graphics memory: 4020638 kiB
[    1.967400] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.967401] [TTM] Initializing pool allocator
[    1.967405] [TTM] Initializing DMA pool allocator
[    1.967422] [drm] radeon: 3072M of VRAM memory ready
[    1.967423] [drm] radeon: 2048M of GTT memory ready.
[    1.967430] [drm] Loading tahiti Microcode
[    1.967521] [drm] Internal thermal controller with fan control
[    1.967571] [drm] probing gen 2 caps for device 8086:340a = 393d02/0
[    1.976765] [drm] radeon: dpm initialized
[    1.978484] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    1.978492] [drm] GART: num cpu pages 524288, num gpu pages 524288
[    1.978544] usbcore: registered new interface driver usbhid
[    1.978546] usbhid: USB HID core driver
[    1.980041] [drm] probing gen 2 caps for device 8086:340a = 393d02/0
[    1.980046] [drm] PCIE gen 2 link speeds already enabled
[    1.980306] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/0003:192F:0416.0001/input/input3
[    1.980407] hid-generic 0003:192F:0416.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[    1.980534] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/0003:413C:2105.0002/input/input4
[    1.992342] [drm] PCIE GART of 2048M enabled (table at 0x00000000002E8000).
[    1.992490] radeon 0000:03:00.0: WB enabled
[    1.992493] radeon 0000:03:00.0: fence driver on ring 0 use gpu addr 0x00000000c0000c00 and cpu addr 0xffff8800351a5c00
[    1.992495] radeon 0000:03:00.0: fence driver on ring 1 use gpu addr 0x00000000c0000c04 and cpu addr 0xffff8800351a5c04
[    1.992496] radeon 0000:03:00.0: fence driver on ring 2 use gpu addr 0x00000000c0000c08 and cpu addr 0xffff8800351a5c08
[    1.992498] radeon 0000:03:00.0: fence driver on ring 3 use gpu addr 0x00000000c0000c0c and cpu addr 0xffff8800351a5c0c
[    1.992499] radeon 0000:03:00.0: fence driver on ring 4 use gpu addr 0x00000000c0000c10 and cpu addr 0xffff8800351a5c10
[    1.993178] radeon 0000:03:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90001435a18
[    2.013204] radeon 0000:03:00.0: fence driver on ring 6 use gpu addr 0x00000000c0000c18 and cpu addr 0xffff8800351a5c18
[    2.013207] radeon 0000:03:00.0: fence driver on ring 7 use gpu addr 0x00000000c0000c1c and cpu addr 0xffff8800351a5c1c
[    2.013217] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.013219] [drm] Driver supports precise vblank timestamp query.
[    2.013221] radeon 0000:03:00.0: radeon: MSI limited to 32-bit
[    2.013246] radeon 0000:03:00.0: radeon: using MSI.
[    2.013274] [drm] radeon: irq initialized.
[    2.034744] hid-generic 0003:413C:2105.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2/input0
[    2.188495] [drm] ring test on 0 succeeded in 1 usecs
[    2.188502] [drm] ring test on 1 succeeded in 1 usecs
[    2.188507] [drm] ring test on 2 succeeded in 1 usecs
[    2.188517] [drm] ring test on 3 succeeded in 3 usecs
[    2.188524] [drm] ring test on 4 succeeded in 3 usecs
[    2.253752] ata7: SATA link down (SStatus 0 SControl 300)
[    2.254176] ata8: SATA link down (SStatus 0 SControl 300)
[    2.265921] random: nonblocking pool is initialized
[    2.364240] usb 10-2: New USB device found, idVendor=2109, idProduct=0810
[    2.364244] usb 10-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.364246] usb 10-2: Product: 4-Port USB 3.0 Hub
[    2.364247] usb 10-2: Manufacturer: VIA Labs, Inc.
[    2.364308] [drm] ring test on 5 succeeded in 1 usecs
[    2.364314] [drm] UVD initialized successfully.
[    2.366385] hub 10-2:1.0: USB hub found
[    2.418278] hub 10-2:1.0: 4 ports detected
[    2.473515] [drm] ring test on 6 succeeded in 20 usecs
[    2.473525] [drm] ring test on 7 succeeded in 3 usecs
[    2.473526] [drm] VCE initialized successfully.
[    2.473785] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.473813] [drm] ib test on ring 1 succeeded in 0 usecs
[    2.473840] [drm] ib test on ring 2 succeeded in 0 usecs
[    2.473866] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.473891] [drm] ib test on ring 4 succeeded in 0 usecs
[    2.773846] usb 10-2.2: new SuperSpeed USB device number 4 using xhci_hcd
[    2.841897] usb 10-2.2: New USB device found, idVendor=059b, idProduct=0070
[    2.841901] usb 10-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.841904] usb 10-2.2: Product: eGo USB
[    2.841906] usb 10-2.2: Manufacturer: Iomega
[    2.841909] usb 10-2.2: SerialNumber: 0100000000015226
[    2.882955] usbcore: registered new interface driver usb-storage
[    2.930368] clocksource: Switched to clocksource tsc
[    2.934492] scsi host8: uas
[    2.934611] usbcore: registered new interface driver uas
[    2.941783] scsi 8:0:0:0: Direct-Access     OEM      Ext Hard Disk    0000 PQ: 0 ANSI: 5
[    3.122481] [drm] ib test on ring 5 succeeded
[    3.190335] scsi 8:0:0:1: CD-ROM            Virtual  CDROM                 PQ: 0 ANSI: 0
[    3.190564] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    3.339442] sd 8:0:0:0: [sdd] 121914886 4096-byte logical blocks: (499 GB/465 GiB)
[    3.385661] sr 8:0:0:1: [sr0] scsi-1 drive
[    3.385665] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.385995] sr 8:0:0:1: Attached scsi CD-ROM sr0
[    3.386079] sr 8:0:0:1: Attached scsi generic sg4 type 5
[    3.576584] sd 8:0:0:0: [sdd] Write Protect is off
[    3.576589] sd 8:0:0:0: [sdd] Mode Sense: 10 00 00 00
[    3.622381] [drm] ib test on ring 6 succeeded
[    3.623642] sd 8:0:0:0: [sdd] Cache data unavailable
[    3.623647] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[    3.817293] sd 8:0:0:0: [sdd] 121914886 4096-byte logical blocks: (499 GB/465 GiB)
[    4.122481] [drm] ib test on ring 7 succeeded
[    4.125405] [drm] Radeon Display Connectors
[    4.125406] [drm] Connector 0:
[    4.125407] [drm]   DP-1
[    4.125408] [drm]   HPD5
[    4.125409] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    4.125410] [drm]   Encoders:
[    4.125411] [drm]     DFP1: INTERNAL_UNIPHY2
[    4.125412] [drm] Connector 1:
[    4.125413] [drm]   HDMI-A-1
[    4.125413] [drm]   HPD4
[    4.125414] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    4.125415] [drm]   Encoders:
[    4.125416] [drm]     DFP2: INTERNAL_UNIPHY2
[    4.125417] [drm] Connector 2:
[    4.125417] [drm]   DVI-D-1
[    4.125418] [drm]   HPD1
[    4.125419] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    4.125420] [drm]   Encoders:
[    4.125420] [drm]     DFP3: INTERNAL_UNIPHY1
[    4.125421] [drm] Connector 3:
[    4.125422] [drm]   DVI-I-1
[    4.125422] [drm]   HPD3
[    4.125424] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    4.125424] [drm]   Encoders:
[    4.125425] [drm]     DFP4: INTERNAL_UNIPHY
[    4.125426] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    4.142967]  sdd: sdd1
[    4.208783] [drm] fb mappable at 0xE06EA000
[    4.208784] [drm] vram apper at 0xE0000000
[    4.208785] [drm] size 8294400
[    4.208786] [drm] fb depth is 24
[    4.208786] [drm]    pitch is 7680
[    4.208943] fbcon: radeondrmfb (fb0) is primary device
[    4.248936] Console: switching to colour frame buffer device 240x67
[    4.250076] sd 8:0:0:0: [sdd] 121914886 4096-byte logical blocks: (499 GB/465 GiB)
[    4.253393] radeon 0000:03:00.0: fb0: radeondrmfb frame buffer device
[    4.262344] [drm] Initialized radeon 2.43.0 20080528 for 0000:03:00.0 on minor 0
[    4.495946] sd 8:0:0:0: [sdd] Attached SCSI disk
[    4.938341] floppy0: no floppy controllers found
[    5.759268] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[    6.609925] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    6.610113] systemd[1]: Detected architecture x86-64.
[    6.625137] systemd[1]: Set hostname to <Sniper-one>.
[    7.956181] systemd[1]: [/lib/systemd/system/neutron-linuxbridge-cleanup.service:5] Unknown lvalue 'type' in section 'Service'
[    8.012409] systemd[1]: Listening on fsck to fsckd communication Socket.
[    8.012484] systemd[1]: Listening on Journal Socket.
[    8.012511] systemd[1]: Listening on Syslog Socket.
[    8.012537] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    8.012558] systemd[1]: Listening on Journal Socket (/dev/log).
[    8.012584] systemd[1]: Listening on udev Control Socket.
[    8.012615] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    8.012710] systemd[1]: Created slice User and Session Slice.
[    8.012732] systemd[1]: Listening on udev Kernel Socket.
[    8.012810] systemd[1]: Created slice System Slice.
[    8.030222] systemd[1]: Starting Uncomplicated firewall...
[    8.030606] systemd[1]: Started Braille Device Support.
[    8.030812] systemd[1]: Reached target Slices.
[    8.031315] systemd[1]: Mounting Debug File System...
[    8.031492] systemd[1]: Created slice system-getty.slice.
[    8.032021] systemd[1]: Mounting POSIX Message Queue File System...
[    8.032441] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    8.032827] systemd[1]: Mounting Huge Pages File System...
[    8.032846] systemd[1]: Reached target Encrypted Volumes.
[    8.032956] systemd[1]: Created slice system-postgresql.slice.
[    8.138423] systemd[1]: Starting Load Kernel Modules...
[    8.138505] systemd[1]: Listening on Journal Audit Socket.
[    8.138900] systemd[1]: Starting Journal Service...
[    8.139395] systemd[1]: Started Read required files in advance.
[    8.139626] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    8.213581] systemd[1]: Reached target Remote File Systems (Pre).
[    8.213601] systemd[1]: Reached target Remote File Systems.
[    8.213624] systemd[1]: Reached target User and Group Name Lookups.
[    8.223041] systemd[1]: Started Uncomplicated firewall.
[    8.223199] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    8.239672] systemd[1]: Starting Create Static Device Nodes in /dev...
[    8.494287] systemd[1]: Mounted Huge Pages File System.
[    8.494421] systemd[1]: Mounted Debug File System.
[    8.494444] systemd[1]: Mounted POSIX Message Queue File System.
[    8.600523] lp: driver loaded but no devices found
[    8.648336] ppdev: user-space parallel port driver
[    8.696471] systemd[1]: Started Journal Service.
[    9.957283] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro
[   10.228011] systemd-journald[316]: Received request to flush runtime journal from PID 1
[   10.740506] EDAC MC: Ver: 3.0.0
[   10.763443] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x000000000000042C-0x000000000000042D (\GP2C) (20160108/utaddress-255)
[   10.763447] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.763470] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.831868] EDAC MC0: Giving out device to module i7core_edac.c controller i7 core #0: DEV 0000:3f:03.0 (POLLED)
[   10.831915] EDAC PCI0: Giving out device to module i7core_edac controller EDAC PCI controller: DEV 0000:3f:03.0 (POLLED)
[   10.831919] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[   10.976958] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.708781] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   11.836847] snd_hda_intel 0000:03:00.1: Handle vga_switcheroo audio client
[   11.836851] snd_hda_intel 0000:03:00.1: Force to non-snoop mode
[   11.876091] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.876799] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input5
[   11.876871] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input6
[   11.876932] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input7
[   11.876998] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input8
[   11.877057] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input9
[   11.877117] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card0/input10
[   11.890737] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.890744] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   11.920755] snd_ctxfi 0000:05:00.0: chip 20K2 model Unknown (1458:a016) is found
[   12.137164] audit: type=1305 audit(1462688135.244:2): audit_pid=626 old=0 auid=4294967295 ses=4294967295 res=1
[   12.204322] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.237247] snd_ctxfi 0000:05:00.0: Use xfi-native timer
[   12.307821] Adding 8787964k swap on /dev/sdc5.  Priority:-1 extents:1 across:8787964k FS
[   12.502018] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.533093] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   12.533803] r8712u: register rtl8712_netdev_ops to netdev_ops
[   12.533807] usb 2-6: r8712u: USB_SPEED_HIGH with 4 endpoints
[   12.534292] usb 2-6: r8712u: Boot from EFUSE: Autoload OK
[   12.801989] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.933103] Adding 9762812k swap on /dev/sdb2.  Priority:-2 extents:1 across:9762812k FS
[   12.953396] usb 2-6: r8712u: CustomerID = 0x000a
[   12.953399] usb 2-6: r8712u: MAC Address from efuse = 00:0d:81:ac:ba:7f
[   12.953401] usb 2-6: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   12.953455] usbcore: registered new interface driver r8712u
[   13.076662] r8712u 2-6:1.0 wlx000d81acba7f: renamed from wlan0
[   13.101951] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   13.401960] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   13.701898] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   13.929967] floppy0: no floppy controllers found
[   14.001939] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[   14.301930] snd_hda_codec_hdmi hdaudioC0D0: HDMI ATI/AMD: no speaker allocation for ELD
[  100.583014] cgroup: new mount options do not match the existing superblock, will be ignored
[  107.746787] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[  107.754743] r8169 0000:08:00.0 enp8s0: link down
[  107.754775] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[  108.233171] IPv6: ADDRCONF(NETDEV_UP): wlx000d81acba7f: link is not ready
[  108.942536] r8712u 2-6:1.0 wlx000d81acba7f: 1 RCR=0x153f00e
[  108.943282] r8712u 2-6:1.0 wlx000d81acba7f: 2 RCR=0x553f00e
[  109.050546] IPv6: ADDRCONF(NETDEV_UP): wlx000d81acba7f: link is not ready
[  110.526648] IPv6: ADDRCONF(NETDEV_UP): wlx000d81acba7f: link is not ready
[  121.390164] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000d81acba7f: link becomes ready
[  123.870916] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[  123.874722] vboxdrv: Found 8 processor cores
[  123.893572] vboxdrv: TSC mode is Invariant, tentative frequency 2798011258 Hz
[  123.893574] vboxdrv: Successfully loaded version 5.0.18_Ubuntu (interface 0x00240000)
[  123.955798] VBoxNetFlt: Successfully started.
[  124.080716] VBoxNetAdp: Successfully started.
[  124.164985] VBoxPciLinuxInit
[  124.249839] vboxpci: IOMMU not found (not registered)
[  127.232102] Bluetooth: Core ver 2.21
[  127.232114] NET: Registered protocol family 31
[  127.232115] Bluetooth: HCI device and connection manager initialized
[  127.232118] Bluetooth: HCI socket layer initialized
[  127.232120] Bluetooth: L2CAP socket layer initialized
[  127.232124] Bluetooth: SCO socket layer initialized
[  127.347118] Netfilter messages via NETLINK v0.30.
[  154.236996] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  154.236999] Bluetooth: BNEP filters: protocol multicast
[  154.237004] Bluetooth: BNEP socket layer initialized
[  253.103005] sd 8:0:0:0: [sdd] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD IN 
[  253.103011] sd 8:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 01 00 00 00 01 00
[  254.122865] sr 8:0:0:1: tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD IN 
[  254.122872] sr 8:0:0:1: tag#1 CDB: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[  254.123090] scsi host8: uas_eh_bus_reset_handler start
[  254.329098] usb 10-2.2: reset SuperSpeed USB device number 4 using xhci_hcd
[  254.749396] scsi host8: uas_eh_bus_reset_handler success
[  255.271900] FAT-fs (sdd1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  255.346878] ISO 9660 Extensions: Microsoft Joliet Level 3
[  255.351953] ISOFS: changing to secondary root
[  434.024196] sd 8:0:0:0: [sdd] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: IN 
[  434.024203] sd 8:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 01 21 00 00 01 00
[  434.024460] scsi host8: uas_eh_bus_reset_handler start
[  434.128278] usb 10-2.2: reset SuperSpeed USB device number 4 using xhci_hcd
[  434.258070] scsi host8: uas_eh_bus_reset_handler success
[  963.941718] perf interrupt took too long (2666 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 4490.440330] [drm:si_dpm_set_power_state [radeon]] *ERROR* si_restrict_performance_levels_before_switch failed
[ 8157.432118] perf interrupt took too long (5051 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 8491.672179] sd 8:0:0:0: [sdd] tag#28 uas_eh_abort_handler 0 uas-tag 29 inflight: CMD IN 
[ 8491.672185] sd 8:0:0:0: [sdd] tag#28 CDB: Read(10) 28 00 00 00 0f c6 00 00 01 00
[ 8491.676627] sd 8:0:0:0: [sdd] tag#27 uas_eh_abort_handler 0 uas-tag 28 inflight: CMD IN 
[ 8491.676633] sd 8:0:0:0: [sdd] tag#27 CDB: Read(10) 28 00 00 00 0f c5 00 00 01 00
[ 8491.682017] sd 8:0:0:0: [sdd] tag#26 uas_eh_abort_handler 0 uas-tag 27 inflight: CMD IN 
[ 8491.682021] sd 8:0:0:0: [sdd] tag#26 CDB: Read(10) 28 00 00 00 0f c4 00 00 01 00
[ 8491.687469] sd 8:0:0:0: [sdd] tag#25 uas_eh_abort_handler 0 uas-tag 26 inflight: CMD IN 
[ 8491.687474] sd 8:0:0:0: [sdd] tag#25 CDB: Read(10) 28 00 00 00 0f c3 00 00 01 00
[ 8491.692888] sd 8:0:0:0: [sdd] tag#24 uas_eh_abort_handler 0 uas-tag 25 inflight: CMD IN 
[ 8491.692896] sd 8:0:0:0: [sdd] tag#24 CDB: Read(10) 28 00 00 00 0f c2 00 00 01 00
[ 8491.698266] sd 8:0:0:0: [sdd] tag#23 uas_eh_abort_handler 0 uas-tag 24 inflight: CMD IN 
[ 8491.698270] sd 8:0:0:0: [sdd] tag#23 CDB: Read(10) 28 00 00 00 0f c1 00 00 01 00
[ 8491.703672] sd 8:0:0:0: [sdd] tag#22 uas_eh_abort_handler 0 uas-tag 23 inflight: CMD IN 
[ 8491.703676] sd 8:0:0:0: [sdd] tag#22 CDB: Read(10) 28 00 00 00 0f c0 00 00 01 00
[ 8491.709123] sd 8:0:0:0: [sdd] tag#21 uas_eh_abort_handler 0 uas-tag 22 inflight: CMD IN 
[ 8491.709129] sd 8:0:0:0: [sdd] tag#21 CDB: Read(10) 28 00 00 00 0f bf 00 00 01 00
[ 8491.714613] sd 8:0:0:0: [sdd] tag#20 uas_eh_abort_handler 0 uas-tag 21 inflight: CMD IN 
[ 8491.714619] sd 8:0:0:0: [sdd] tag#20 CDB: Read(10) 28 00 00 00 0f be 00 00 01 00
[ 8491.720002] sd 8:0:0:0: [sdd] tag#19 uas_eh_abort_handler 0 uas-tag 20 inflight: CMD IN 
[ 8491.720006] sd 8:0:0:0: [sdd] tag#19 CDB: Read(10) 28 00 00 00 0f bd 00 00 01 00
[ 8491.725409] sd 8:0:0:0: [sdd] tag#18 uas_eh_abort_handler 0 uas-tag 19 inflight: CMD IN 
[ 8491.725413] sd 8:0:0:0: [sdd] tag#18 CDB: Read(10) 28 00 00 00 0f bc 00 00 01 00
[ 8491.730830] sd 8:0:0:0: [sdd] tag#17 uas_eh_abort_handler 0 uas-tag 18 inflight: CMD IN 
[ 8491.730836] sd 8:0:0:0: [sdd] tag#17 CDB: Read(10) 28 00 00 00 0f bb 00 00 01 00
[ 8491.736232] sd 8:0:0:0: [sdd] tag#16 uas_eh_abort_handler 0 uas-tag 17 inflight: CMD IN 
[ 8491.736239] sd 8:0:0:0: [sdd] tag#16 CDB: Read(10) 28 00 00 00 0f ba 00 00 01 00
[ 8491.741698] sd 8:0:0:0: [sdd] tag#15 uas_eh_abort_handler 0 uas-tag 16 inflight: CMD IN 
[ 8491.741703] sd 8:0:0:0: [sdd] tag#15 CDB: Read(10) 28 00 00 00 0f b9 00 00 01 00
[ 8491.747116] sd 8:0:0:0: [sdd] tag#14 uas_eh_abort_handler 0 uas-tag 15 inflight: CMD IN 
[ 8491.747122] sd 8:0:0:0: [sdd] tag#14 CDB: Read(10) 28 00 00 00 0f b8 00 00 01 00
[ 8491.752537] sd 8:0:0:0: [sdd] tag#13 uas_eh_abort_handler 0 uas-tag 14 inflight: CMD IN 
[ 8491.752543] sd 8:0:0:0: [sdd] tag#13 CDB: Read(10) 28 00 00 00 0f b7 00 00 01 00
[ 8491.757958] sd 8:0:0:0: [sdd] tag#12 uas_eh_abort_handler 0 uas-tag 13 inflight: CMD IN 
[ 8491.757962] sd 8:0:0:0: [sdd] tag#12 CDB: Read(10) 28 00 00 00 0f b6 00 00 01 00
[ 8491.763372] sd 8:0:0:0: [sdd] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD IN 
[ 8491.763375] sd 8:0:0:0: [sdd] tag#11 CDB: Read(10) 28 00 00 00 0f b5 00 00 01 00
[ 8491.768807] sd 8:0:0:0: [sdd] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD IN 
[ 8491.768812] sd 8:0:0:0: [sdd] tag#10 CDB: Read(10) 28 00 00 00 0f b4 00 00 01 00
[ 8491.774263] sd 8:0:0:0: [sdd] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD IN 
[ 8491.774268] sd 8:0:0:0: [sdd] tag#9 CDB: Read(10) 28 00 00 00 0f b3 00 00 01 00
[ 8491.779733] sd 8:0:0:0: [sdd] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD IN 
[ 8491.779739] sd 8:0:0:0: [sdd] tag#8 CDB: Read(10) 28 00 00 00 0f b2 00 00 01 00
[ 8491.785139] sd 8:0:0:0: [sdd] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD IN 
[ 8491.785145] sd 8:0:0:0: [sdd] tag#7 CDB: Read(10) 28 00 00 00 0f b1 00 00 01 00
[ 8491.790584] sd 8:0:0:0: [sdd] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD IN 
[ 8491.790589] sd 8:0:0:0: [sdd] tag#6 CDB: Read(10) 28 00 00 00 0f b0 00 00 01 00
[ 8491.796011] sd 8:0:0:0: [sdd] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD IN 
[ 8491.796016] sd 8:0:0:0: [sdd] tag#5 CDB: Read(10) 28 00 00 00 0f af 00 00 01 00
[ 8491.801426] sd 8:0:0:0: [sdd] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD IN 
[ 8491.801432] sd 8:0:0:0: [sdd] tag#4 CDB: Read(10) 28 00 00 00 0f ae 00 00 01 00
[ 8491.806899] sd 8:0:0:0: [sdd] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD IN 
[ 8491.806904] sd 8:0:0:0: [sdd] tag#3 CDB: Read(10) 28 00 00 00 0f ad 00 00 01 00
[ 8491.812356] sd 8:0:0:0: [sdd] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD IN 
[ 8491.812362] sd 8:0:0:0: [sdd] tag#2 CDB: Read(10) 28 00 00 00 0f ac 00 00 01 00
[ 8491.817771] sd 8:0:0:0: [sdd] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD IN 
[ 8491.817777] sd 8:0:0:0: [sdd] tag#1 CDB: Read(10) 28 00 00 00 0f ab 00 00 01 00
[ 8491.823187] sd 8:0:0:0: [sdd] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD IN 
[ 8491.823194] sd 8:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 0f aa 00 00 01 00
[ 8493.652132] sr 8:0:0:1: tag#29 uas_eh_abort_handler 0 uas-tag 30 inflight: CMD IN 
[ 8493.652138] sr 8:0:0:1: tag#29 CDB: Get event status notification 4a 01 00 00 10 00 00 00 08 00
[ 8493.655879] scsi host8: uas_eh_bus_reset_handler start
[ 8493.767714] usb 10-2.2: reset SuperSpeed USB device number 4 using xhci_hcd
[ 8494.285238] scsi host8: uas_eh_bus_reset_handler success
[10261.661137] IPv6: ADDRCONF(NETDEV_UP): wlx000d81acba7f: link is not ready
[10261.711294] IPv6: ADDRCONF(NETDEV_UP): wlx000d81acba7f: link is not ready
[10272.159433] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000d81acba7f: link becomes ready

freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.5.0-040500rc7-generic x86_64 (64 bit) Desktop: Gnome 3.18.4
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2794 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.18.3 drivers: ati,vesa (unloaded: fbdev,radeon) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.8.0) GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169
           Card-2: Realtek RTL8191SU 802.11n WLAN Adapter driver: r8712u
Drives:    HDD Total Size: 4250.1GB (5.6% used)
Info:      Processes: 338 Uptime: 3:27 Memory: 2443.3/7852.8MB Client: Shell (bash) inxi: 2.2.35 

 
```

---

### Post by valereguerin on 2016-05-08
i surf too quickly with !  my live cd on my toshiba portable computer ! i5 4096 ram 30/60 times more quickly !!!!

i think internet libsssssss pb , it's the same with 14.04 (unity) connections pb pb pb (Secure connection failed ! too often ! 5 minutes to see video !  cache 1024 ! the video not load correctly PPPFFFFFUUUUUUUUUUUUUUU!!!!!!!!

16.04 not good  14.04 not good, 12.04 ????????maybe......run run to 38.04 !!!!run !!!!!

15.10 the SAME ! HHHHHaaaaaaaaaaaargGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGggg

---

### Post by PJs Ronin on 2016-05-08
I notice you're running 2 PostgreSQL servers, is there a specific need for both/any?

I also had problems with *NetworkManager-wait-online.service* slowing my boot sequence for no apparent good reason.   I removed it, halved my boot time and had no injuries.   You may care to try: ```
sudo systemctl disable NetworkManager-wait-online.service
```
and if no benefit, then turn it back on via:```
sudo systemctl enable NetworkManager-wait-online.service
```
I believe it is best to do a full reboot to implement these changes.

There are some interesting discussions [here]("https://ask.fedoraproject.org/en/question/33515/fedora19-improving-boot-timedisabling-useless-services/") and [here]("http://unix.stackexchange.com/questions/235797/which-processes-are-not-needed-for-boot") with guidance about disabling *plymouth-quit-wait.service*.

---

### Post by PJs Ronin on 2016-05-08
I'm not sure this is a 16.10 problem... Mods may care to review.

---

### Post by vasa1 on 2016-05-08
> **PJs Ronin said:**
> I'm not sure this is a 16.10 problem... Mods may care to review.

+1. Thank you for pointing that out. Moved to General Help.

---

### Post by valereguerin on 2016-05-09
after the end of the : update / upgrade / dist-upgrade ; this morning everything is ok (for the moment....)on 16.04 and 14.04 i don't boot 15.10 yet this morning  
```
 freeman@Sniper-one:~$ systemd-analyze blame
         48.395s plymouth-quit-wait.service
         18.239s postgresql@9.5-main.service
         18.151s postgresql@9.4-main.service
         18.041s apt-cacher.service
         16.485s NetworkManager-wait-online.service
          7.976s postfix.service
          7.694s ModemManager.service
          7.218s teamviewerd.service
          6.004s NetworkManager.service
          5.659s ntop.service
          5.455s kdump-tools.service
          4.971s samhain.service
          4.614s dev-sdc3.device
          4.208s collectl.service
          4.102s apparmor.service
          4.075s vboxweb.service
          3.952s accounts-daemon.service
lines 1-17

```

PJS Ronin said :I notice you're running 2 PostgreSQL servers, is there a specific need for both/any?

no ! after update, my system don't want uninstall 9.4 !

---

### Post by valereguerin on 2016-05-09
> **sudodus said:**
> If systemd is unhappy with something, there is a delay of 1 min 30 s. Maybe you are affected by it. Boot without the boot options 'quiet splash' and watch the text on the screen. Maybe it will show what is the problem.

not journalsssssssssssss -system ? for "to know " where the problem is :confused:

"journal-Boot" not exist ? (the last "5" for exemple (for compare....)  :(:()

a command-Line ?

!!!! Hello Community !!!!! i'm nervous with the situation of our world and the update-compilation of my system ; i forget essential thing !

i find !......i don't put my computer off......but when i want to go on my othersss system is not coooool, you see what i mean ?

---

