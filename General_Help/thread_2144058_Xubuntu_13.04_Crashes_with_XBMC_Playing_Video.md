---
title: "Xubuntu 13.04 Crashes with XBMC Playing Video"
date: 2013-05-11
forum: General Help
---

### Post by driekus on 2013-05-11
Hi All, 
I recently built a new server (10 days ago) with a Xeon 1230 V2 and an Asus P8Z77 V LX motherboard. The Video Card is GT640 with video plugged into VGA port.
I originally installed Linux Mint 14 XFCE (Based on Ubuntu 13.04) and moved up to Xubuntu 13.04. Both installs have had the same problem. While playing XBMC video it has crashed once on each of the systems. 
I took a look at the kern.log and have uploaded areas that I think may be relevant. Any assistance I would be eternally grateful.

May 10 21:23:59 peter-System-Product-Name kernel: [    1.834706] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834712] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834715] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834718] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834720] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834722] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May 10 21:23:59 peter-System-Product-Name kernel: [    1.834724] lpc_ich: Resource conflict(s) found affecting gpio_ich

May 10 21:23:59 peter-System-Product-Name kernel: [    3.855979] NVRM: Your system is not currently configured to drive a VGA console
May 10 21:23:59 peter-System-Product-Name kernel: [    3.855982] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
May 10 21:23:59 peter-System-Product-Name kernel: [    3.855983] NVRM: requires the use of a text-mode VGA console. Use of other console
May 10 21:23:59 peter-System-Product-Name kernel: [    3.855984] NVRM: drivers including, but not limited to, vesafb, may result in
May 10 21:23:59 peter-System-Product-Name kernel: [    3.855985] NVRM: corruption and stability problems, and is not supported.
May 10 21:24:00 peter-System-Product-Name kernel: [    4.892625] r8169 0000:03:00.0 eth0: link up
May 10 21:24:00 peter-System-Product-Name kernel: [    4.892632] IPv6: ADDRCONF(NETDEV_CHANGE):

---

