---
title: "[xubuntu 18.04] Reboot instead of shutdown"
date: 2018-04-29
forum: General Help
---

### Post by login721 on 2018-04-29
Hello . I have problem with shutdown with xubuntu 18.04.Every time i shutdown (event with sudo shutdown -P now) , the pc will auto reboot a few seconds after shutdown .
I tried added "acpi=noirq" option to GRUB_CMDLINE_LINUX_DEFAULT but it didn't help .Only disable WOL in bios works.But i need WOL , is there any way to shutdown normally when WOL enabled ? 
Thanks in advance!
Sorry for my bad English!

---

### Post by ajgreeny on 2018-04-29
Try command ```
shutdown -H now
``` without sudo which is no longer required for a shutdown or reboot.
I know the -P and -H options should both work the same (more or less; not sure what exactly the difference is) but -H is worth a try.

---

### Post by login721 on 2018-05-02
Thank you! work like a charm.

---

