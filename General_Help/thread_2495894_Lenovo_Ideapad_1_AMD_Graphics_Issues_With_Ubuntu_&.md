---
title: "Lenovo Ideapad 1 AMD Graphics Issues With Ubuntu &gt;23.04"
date: 2024-03-06
forum: General Help
---

### Post by PBK on 2024-03-06
I have a Lenovo IdeaPad 1 15AMN7 with AMD Radeon graphics. Ubuntu 23.04 works just fine, but when trying Ubuntu 23.10 or a recent 24.04 download, I have graphics issues.

I have tried resetting BIOS, but no-go. Trying Ubuntu 24.04, I see that the screen resolution and refresh rate are the same as the working Ubuntu 23.04: 1920x1080 and 60Hz.

Running lshw -c video lets me know that both working and not working Ubuntu are loading the amdgpu driver.

If I select Safe Graphics during boot with 24.04, screen seems fine and uses 77Hz refresh rate and also does not load the amdgpu driver.

What am I doing wrong? Anything I can do to get relief?

Thanks

(Cross posted on Lenovo Forum)

[ATTACH=CONFIG]293463[/ATTACH]

---

