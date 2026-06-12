---
title: "No Keyboard Input on Resume"
date: 2007-10-22
forum: General Help
---

### Post by rfdeshon on 2007-10-22
Okay, I have a doozy of a problem here. After my laptop comes back from hibernation, SOMETIMES, the xscreensaver lock will not let me type anything in the password box. If I click on "Switch User" it will go back to the login screen and I can log back in just fine. Then I can lock the screen and type my password in just fine. Has anyone heard of people having this problem before? Is it fixable? Should I file a bug report?

Don't know if it will help, but here is my output from /var/log/messages after one of these sessions:
```
Oct 22 15:51:35 lappy486 gnome-power-manager: (rfdeshon) Resuming computer
Oct 22 15:51:35 lappy486 kernel: [122644.600000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 22 15:51:35 lappy486 kernel: [122644.600000] sd 0:0:0:0: [sda] Write Protect is off
Oct 22 15:51:35 lappy486 kernel: [122644.600000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 15:51:35 lappy486 kernel: [122645.072000] sd 0:0:0:0: [sda] Starting disk
Oct 22 15:51:37 lappy486 kernel: [122647.316000] 8139too Fast Ethernet driver 0.9.28
Oct 22 15:51:37 lappy486 kernel: [122647.316000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Oct 22 15:51:37 lappy486 kernel: [122647.320000] eth0: RealTek RTL8139 at 0xf89ee000, 00:0f:b0:c8:71:e3, IRQ 21
Oct 22 15:51:37 lappy486 kernel: [122647.364000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Oct 22 15:51:37 lappy486 kernel: [122647.364000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct 22 15:51:37 lappy486 kernel: [122647.400000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
Oct 22 15:51:37 lappy486 kernel: [122647.400000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Oct 22 15:51:37 lappy486 kernel: [122647.404000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 22 (level, low) -> IRQ 23
Oct 22 15:51:37 lappy486 kernel: [122647.404000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Oct 22 15:51:38 lappy486 kernel: [122647.708000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Oct 22 15:51:39 lappy486 kernel: [122649.276000] input: Power Button (FF) as /class/input/input19
Oct 22 15:51:39 lappy486 kernel: [122649.280000] ACPI: Power Button (FF) [PWRF]
Oct 22 15:51:39 lappy486 kernel: [122649.308000] input: Lid Switch as /class/input/input20
Oct 22 15:51:39 lappy486 kernel: [122649.308000] ACPI: Lid Switch [LID0]
Oct 22 15:51:39 lappy486 kernel: [122649.364000] input: Power Button (CM) as /class/input/input21
Oct 22 15:51:39 lappy486 kernel: [122649.364000] ACPI: Power Button (CM) [PWRB]
Oct 22 15:51:40 lappy486 kernel: [122650.564000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 22 15:51:40 lappy486 kernel: [122650.564000] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 22 15:51:40 lappy486 kernel: [122650.672000] ACPI: AC Adapter [ACAD] (on-line)
Oct 22 15:51:41 lappy486 kernel: [122650.864000] ACPI: Battery Slot [BAT1] (battery present)
Oct 22 15:51:45 lappy486 kernel: [122655.504000] eth0: link down
Oct 22 15:51:45 lappy486 kernel: [122655.508000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 22 15:51:57 lappy486 kernel: [122666.804000] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
Oct 22 15:52:11 lappy486 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Oct 22 15:52:11 lappy486 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers

```

Is there anything else that could help with this?

---

