---
title: "editing grub bootloader"
date: 2007-06-19
forum: General Help
---

### Post by cptjaben on 2007-06-19
I just reinstalled Edgy on my laptop. Previously, grub would load up with when my computer booted up and it would give me 3 seconds to press Esc which would take to me the screen in which i could choose what OS to run, and if not would directly load me to Ubuntu. Now when Grub loads up it waits around 6-8 seconds with that screen open. Since i rarely use Windows, i was wondering if anyone knows how to change grub to the previous setting or just decrease the time to choose. Thanks

---

### Post by kevinlyfellow on 2007-06-19
Look for the timeout option in /boot/grub/menu.lst  It should look something like this (after you set it for 3 seconds)

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

```

---

### Post by cptjaben on 2007-06-19
Thanks much for the help.

---

