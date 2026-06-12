---
title: "dmesg yoyo failed"
date: 2021-01-28
forum: General Help
---

### Post by VMC on 2021-01-28
[FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#18b218]**$**[/COLOR][COLOR=#000000] sudo dmesg|grep yoyo[/COLOR]
[/FONT][/FONT][/FONT]```
[FONT=monospace][COLOR=#000000]wlwifi 0000:00:14.3: Direct firmware load for iwl-debug-[/COLOR][COLOR=#ff5454]**yoyo**[/COLOR][COLOR=#000000].bin failed with error [/COLOR]-2[/FONT]
```[FONT=monospace]

Does anyone else see this? Apparently its been logged sever times.
I found this info
[https://patchwork.kernel.org/project/linux-wireless/patch/20200625165210.14904-1-wsa@kernel.org/](https://patchwork.kernel.org/project/linux-wireless/patch/20200625165210.14904-1-wsa@kernel.org/)
Some sort of patch here:
[https://www.spinics.net/lists/linux-wireless/msg201184.html](https://www.spinics.net/lists/linux-wireless/msg201184.html)
[/FONT]

---

