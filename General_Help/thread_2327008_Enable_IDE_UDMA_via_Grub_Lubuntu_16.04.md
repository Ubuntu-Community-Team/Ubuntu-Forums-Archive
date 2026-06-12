---
title: "Enable IDE UDMA via Grub Lubuntu 16.04"
date: 2016-06-06
forum: General Help
---

### Post by roler2 on 2016-06-06
I have tried to enable UDMA however I keep receiving an error message:

[B]HDIO_GET_DMA failed: Inappropriate ioctl for device

[/B]Is there a way to enable UDMA via Grub?

I read to add these two lines in etc/modules above the line ide-cd for Intel CPU:

piix
ide-core

However there is no line ide-cd in etc/modules.

Please advise if possible. Thank you!

---

