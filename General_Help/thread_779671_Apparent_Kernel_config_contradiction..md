---
title: "Apparent Kernel config contradiction."
date: 2008-05-02
forum: General Help
---

### Post by jtappin on 2008-05-02
I have a rather elderly [ca. 1998] BusLogic Flashpoint SCSI card, which has a DDS3 internal tape drive hanging off it.

I recently upgraded most of my hardware to an Athlon 64 X2 (in place of the old Athlon XP) and also upgraded from Gutsy to Hardy.

Prior to that (going back to Warty or Breezy [and other distros back to SuSE 5.2]) the hardware combination worked fine.

Now however there are no SCSI tape devices, and the "st" module is not loaded, "BusLogic" is loaded. The tape drive does not show up in /proc/scsi/scsi, though the controller shows up in lspci.

The main clues that I can find are in /var/log/syslog I see:
```

May  2 18:38:53 xena kernel: [   27.673294] BusLogic: FlashPoint Host Adapter detected at PCI Bus 1 Device 6
May  2 18:38:53 xena kernel: [   27.673297] BusLogic: I/O Address 0x9C00 PCI Address 0xFDEFF000, irq 16, but FlashPoint
May  2 18:38:53 xena kernel: [   27.673298] BusLogic: support was omitted in this kernel configuration.

```

But in /boot/config-2.6.24-16-generic (which is the kernel I'm running) it says (*inter alia*):
```

# CONFIG_SCSI_OMIT_FLASHPOINT is not set

```
which appears to contradict the system log. Any clues?

P.S. The tape drive is seen by the BIOS (Python ARCHIVE) so it can't be a connection issue.

---

### Post by jtappin on 2008-05-08
Looks like it's a 64-bit related kernel problem:
[http://bugzilla.kernel.org/show_bug.cgi?id=10226](http://bugzilla.kernel.org/show_bug.cgi?id=10226)

(And apparently the driver has no maintainer).

---

