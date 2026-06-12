---
title: "GPU HANG: EVDI to blame?"
date: 2023-01-29
forum: General Help
---

### Post by benjaminbreeg on 2023-01-29
[COLOR=#24292F][FONT=-apple-system]Could the GPU HANG below have been caused by evdi? [/FONT][/COLOR]
```
[COLOR=#24292F][FONT=-apple-system]Jan 29 10:27:42 DadsLGGram kernel: [56135.623486] evdi: [I] (card2) Notifying display power state: on
Jan 29 10:27:42 DadsLGGram kernel: [57002.621366] i915 0000:00:02.0: [drm] GPU HANG: ecode 12:1:859ffffb, in gnome-shell [8434]
Jan 29 10:27:42 DadsLGGram kernel: [57002.621415] i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
Jan 29 10:27:42 DadsLGGram kernel: [57002.725048] i915 0000:00:02.0: [drm] gnome-shell[8434] context reset due to GPU hang
Jan 29 10:27:42 DadsLGGram kernel: [57002.725110] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.bin version 70.5.1
Jan 29 10:27:42 DadsLGGram kernel: [57002.725112] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9.3
Jan 29 10:27:42 DadsLGGram kernel: [57002.743253] i915 0000:00:02.0: [drm] HuC authenticated
Jan 29 10:27:42 DadsLGGram kernel: [57002.743891] i915 0000:00:02.0: [drm] GuC submission enabled
Jan 29 10:27:42 DadsLGGram kernel: [57002.743892] i915 0000:00:02.0: [drm] GuC SLPC enabled
[/FONT][/COLOR]

```

[COLOR=#24292F][FONT=-apple-system][These are my system's details]("https://paste.ubuntu.com/p/Q2YDy5Qp7M/"), as requested.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-01-29
Try this first: [https://ubuntuforums.org/showthread.php?t=2483059&p=14126973#post14126973](https://ubuntuforums.org/showthread.php?t=2483059&p=14126973#post14126973)
If that doesn't work, switch from using Wayland to Xorg in the GDM logon sessions selector (gear icon)...

---

### Post by benjaminbreeg on 2023-01-29
> **MAFoElffen said:**
> Try this first: [https://ubuntuforums.org/showthread.php?t=2483059&p=14126973#post14126973](https://ubuntuforums.org/showthread.php?t=2483059&p=14126973#post14126973)
If that doesn't work, switch from using Wayland to Xorg in the GDM logon sessions selector (gear icon)...
Thank you! I did that, and so far so good! No crashes yet, though it's not easy to tell when they might happen. At any rate, one interesting side effect is that my CPU temperature is now much lower: before applying his trick the average CPU temp was 85C, and [now it hovers around 60C!]("https://www.displaylink.org/forum/showthread.php?t=68592")

---

### Post by MAFoElffen on 2023-01-30
Did the boot parameter 'i915.enable_psr2_sel_fetch=0' lower the tempz/ Or using Xorg? That difference in GPU temp (25C) is quite significant, and I am very curious about that...

---

### Post by benjaminbreeg on 2023-01-30
> **MAFoElffen said:**
> Did the boot parameter 'i915.enable_psr2_sel_fetch=0' lower the tempz/ Or using Xorg? That difference in GPU temp is quite significant, and I am very curious about that...
I only did the boot parameter. If I come across any more GPU freezes in the future, I will attempt the second fix you recommended. (Here's hoping I won't need to!) In the meantime, can I get your input about [this]("https://ubuntuforums.org/showthread.php?t=2483447&p=14128699#post14128699") please?

Many thanks again for your attention to these matters!

---

