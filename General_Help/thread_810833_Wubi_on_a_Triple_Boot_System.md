---
title: "Wubi on a Triple Boot System?"
date: 2008-05-28
forum: General Help
---

### Post by capatt on 2008-05-28
Hello
    I currently have a triple boot system:  XP, Vista, PCLinuxOS.  I'd like to install Ubuntu 8.04 via Wubi but am worried about how it will coexist with my current boot arrangement and the added complexity.  

My setup:
C:\XP, and sda5/swap/sda7 for PCLinuxOS
D:\Vista
Boot loader on C:\configured with EasyBCD

Any suggestions on how best to approach this?

Thanks

---

### Post by ago on 2008-05-29
Just run wubi under either vista or XP, it should add an entry to their bootloader.

---

