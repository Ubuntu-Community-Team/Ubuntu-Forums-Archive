---
title: "Suspend bug in kernel 5.8.0-43-generic"
date: 2021-02-21
forum: General Help
---

### Post by emilio-11 on 2021-02-21
[LEFT][COLOR=#242729][FONT=Arial]For the past few days, I've been dealing with suspend issues happening in my Ubuntu OS 20.04. Due to some reasons, resuming after suspend does not work sometimes. I've checked kernel logs and noticed following log message

[/FONT][/COLOR][/LEFT]> [COLOR=#ff0000]**x86/pm: family 0x16 cpu detected, MSR saving is needed during suspending**[/COLOR][LEFT][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]I previously thought that recent kernel update could be a root cause but after downgrading to previous kernels nothing changed. Does anyone has an idea what could be a reason for this?[/FONT][/COLOR][/LEFT]

---

