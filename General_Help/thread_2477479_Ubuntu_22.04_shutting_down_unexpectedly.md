---
title: "Ubuntu 22.04 shutting down unexpectedly"
date: 2022-07-26
forum: General Help
---

### Post by sanskritsuthar on 2022-07-26
Ubuntu 22.04 is shutting down unexpectedly. I have been using Ubuntu for two months now. I was not facing this issue but since the last week, Ubuntu is shutting down unexpectedly. After booting, I see Recovering Journal on my screen. Can someone please help? How do I provide logs?

---

### Post by #&amp;thj^% on 2022-07-26
If you can, try this one in the terminal:
```
sudo dmesg | grep -i -E 'error|warn|failed' >dmesg.txt
```
That file will be printed to your home directory, named "dmesg.txt"

---

### Post by sanskritsuthar on 2022-07-27
[    2.036753] RAS: Correctable Errors collector initialized.
[    2.303082] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20210730/utaddress-204)
[    2.303092] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20210730/utaddress-204)
[    2.303097] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20210730/utaddress-204)
[    2.303101] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20210730/utaddress-204)
[   14.673172] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro. Quota mode: none.

---

