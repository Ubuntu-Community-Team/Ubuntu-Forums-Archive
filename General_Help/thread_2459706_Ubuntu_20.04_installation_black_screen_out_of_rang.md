---
title: "Ubuntu 20.04 installation black screen out of range"
date: 2021-03-24
forum: General Help
---

### Post by aug7744 on 2021-03-24
When trying to install 20.04 64 bits the LCD screen is black with message out of range. Possibly is using an not compatible resolution. How to edit configuration (xorg) to change resolution and refresh rate to 1368X768 60 HZ ? Thanks for your reply.

---

### Post by bcschmerker on 2021-03-27
**What are the make and model of System Unit, Video Display Adapter, and Display Unit?**  I've a hunch that your Display Unit is not up to the VDA's capacities, in which case ye need the Recovery Menu to access the necessary Config files (on POST, pin left shift until GRUB Menu; down, return, down, return, if the GRUB Menu is unreadable).  There are two files that need amendment:  /etc/default/grub:  ```
...
GRUB_DEFAULT=0
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_CMDLINE_LINUX_DEFAULT=""
...
GRUB_TERMINAL=console
...
GRUB_INIT_TUNE="480 880 1"
```and /etc/X11/xorg.conf, which in X11 relies on autoconfiguation; I'm rusty on overriding Modes on a Screen, so won't post a second Codebox for the necessary Sections.

---

### Post by ActionParsnip on 2021-03-27
Does the system have a make and model?

---

