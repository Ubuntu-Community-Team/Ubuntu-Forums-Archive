---
title: "Samsung Galaxy Book SM-W620 - Boot to BIOS from xubuntu?"
date: 2018-01-28
forum: General Help
---

### Post by makem2 on 2018-01-28
I have just bought the above machine with the intention of dual booting xubunto with the installed windows 10. When accessing the BIOS with the F2 key the only choices available were, windows boot manager or 'disabled' with the existing options relating to fast boot etc. The only way I could find to boot from USB was to turn off the fastboot etc and select 'disabled'.

I can now only boot to USB. Is there a terminal command to allow booting to BIOS from xubuntu, I found the suggestion below but not sure if it would work in my case.

[https://ubuntuforums.org/showthread.php?t=2199257](https://ubuntuforums.org/showthread.php?t=2199257)

```
[COLOR=#000000]Do you have UEFI and this entry in grub menu? That should boot into UEFI.[/COLOR]

[COLOR=#000000]### BEGIN /etc/grub.d/30_uefi-firmware ###[/COLOR]
[COLOR=#000000]menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {[/COLOR]
[COLOR=#000000]fwsetup[/COLOR]
[COLOR=#000000]}[/COLOR]
```

EDIT: This is what/etc/default/grub contains:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by makem2 on 2018-01-28
Think before posting!!!!

Reboot holding down the F2 key! :redface:

---

