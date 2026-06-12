---
title: "Gutsy can't boot"
date: 2008-02-03
forum: General Help
---

### Post by damir_1105 on 2008-02-03
Ubuntu Gutsy: system was up about 12 days, last update(kdebase, etc) i remeber was last night. Today, work in shell start producing errors. After cat something or chmod some file i got Segmenation fault error. I try restarting mashine but after that system would't boot, while loading services i got many Segmentation faults, failsafe don't work either. I have 3 kernel images but its same error on all of them.

Now i'm on live cd and i can't find anything strange in /var/log/ that showing errors. only thing i have is core dump file. i will provide these logs if anybody knows where to find them. :)

---

### Post by damir_1105 on 2008-02-04
I athached appport log. does anyone know what producing these errors. I trying to fix it from live cd using chroot.

---

### Post by damir_1105 on 2008-02-04
live cd chroot to unfunctional /
using zsh
```
ubuntu# bash
zsh: segmentation fault (core dumped)  bash
ubuntu# cat
zsh: segmentation fault (core dumped)  cat
ubuntu# chmod
zsh: segmentation fault (core dumped)  chmod
```

any idea how to fix. i try reconfiguring libc6, coreutils, same problems again.

---

