---
title: "Ubuntu 18.10 freezes on boot after kernel upgrade"
date: 2018-12-27
forum: General Help
---

### Post by lovro2 on 2018-12-27
[SIZE=4]**TL;DR**[/SIZE]

A few days ago my kernel got upgraded from *4.18.0-12-generic* to *4.18.0-13-generic*, now the boot process freezes, regardless of which kernel I choose in GRUB. **Recovery mode still works**.

Computer: Dell XPS 15 9560
OS: Ubuntu 18.10, dual boot with Windows 10
Encryption: Yes, full system encryption on Ubuntu using LVM / LUKS

[HR][/HR]
[SIZE=4]**Details**[/SIZE]

When trying to boot into either of the kernels and pressing *Escape* to show the log I see the same message at the top every time:
```

  WARNING: Failed to connect to lvmetad. Falling back to device scanning.  Volume group "system" not found
  Cannot process volume group system
WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
cryptsetup: system: set up successfully
root: recovering journal
root: clean, 783658/25985024 files, 9547462/103928832 blocks

```

I'm not sure if it has anything to do with the problem, because after this the boot process continues. The log fills up with entries ending with *.mount* and *.service*, but then it suddenly stops and freezes.
Sometimes a kernel panic shows up:

```

Kernel panic - not syncing: Timeout: Not all CPUs entered broadcast exception handler
Shutting down cpus with NMI
Kernel Offset: 0xd200000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
Rebooting in 30 seconds..

```

I already played around with nvidia drivers - uninstalled, reconfigured, reinstalled them, but nothing helped. I also added *noresume* and *nomodeset *to grub, though it had no effect.
When I installed Ubuntu alongside Windows I followed this guide to enable full system encryption - [https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption). Everything has been working perfectly until now.

My current grub config:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_rev_override=1 pci=nomsi noresume nomodeset"
GRUB_CMDLINE_LINUX=""


GRUB_GFXMODE=640x480,800x600,1024x768,1280x1024,1600x1200,1920x1440
GRUB_GFXPAYLOAD_LINUX=keep
GRUB_TERMINAL_OUTPUT="gfxterm"


GRUB_ENABLE_CRYPTODISK=y

```

Any help would be greatly appreciated, I already ran out of ideas.

---

