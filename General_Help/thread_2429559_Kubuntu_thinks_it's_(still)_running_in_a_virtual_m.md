---
title: "Kubuntu thinks it's (still) running in a virtual machine"
date: 2019-10-19
forum: General Help
---

### Post by zazizu on 2019-10-19
[B]
edit: There was nothing wrong - journalctl was just showing really old logs. I scrolled to the end, and there is nothing about VMware.
[/B](post can be deleted)


[COLOR=#d3d3d3]Original post:
I wanted to install Kubuntu on an external HDD, so I made a VM in VMware, attached the external HDD as a physical drive, and installed Kubuntu with an ISO.
The installation went great, and the external HDD boots properly when it's outside of the VM.

The problem is, when I boot from the HDD and run journalctl, I can still see lines like these:

```

Eki 11 22:42:29 expansion1 kernel: efi: EFI v2.31 by VMware, Inc.
Eki 11 22:42:29 expansion1 kernel: efi:  SMBIOS=0xdf86000  ACPI 2.0=0xbb06000  MEMATTR=0xbc09298
...
Eki 11 22:42:29 expansion1 kernel: DMI: VMware, Inc. VMware7,1/440BX Desktop Reference Platform, BIOS VMW71.00V.6997262.B64.1710270607 10/27/2017
Eki 11 22:42:29 expansion1 kernel: Hypervisor detected: VMware
Eki 11 22:42:29 expansion1 kernel: vmware: TSC freq read from hypervisor : 2201.000 MHz
Eki 11 22:42:29 expansion1 kernel: vmware: Host bus clock speed read from hypervisor : 66000000 Hz
Eki 11 22:42:29 expansion1 kernel: vmware: using sched offset of 18604731451 ns
...
Eki 11 22:42:29 expansion1 kernel: Booting paravirtualized kernel on VMware hypervisor
...
Eki 11 22:42:30 expansion1 systemd[1]: Detected virtualization vmware.
...
Eki 11 22:42:30 expansion1 systemd[1]: Mounting VMware vmblock fuse mount...
...
Eki 11 22:42:52 expansion1 systemd[1]: Started Service for virtual machines hosted on VMware.

```

Is there a way to get rid of these? Like, how can I make it realize that it's no longer running in a VM?
I'm not going to boot that VM from this HDD anymore, so I don't mind if fixing this issue breaks VMware functionality in the process.

I'm aware that this is quite an edge-case, but I would highly appreciate if some of you could provide a little help.[/COLOR]

---

