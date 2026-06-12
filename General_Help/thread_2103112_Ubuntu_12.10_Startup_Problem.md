---
title: "Ubuntu 12.10 Startup Problem"
date: 2013-01-09
forum: General Help
---

### Post by rj7 on 2013-01-09
Hi,
I have dell laptop with triple boot. I have Win 7, Ubuntu 12.10 and Ubuntu 10.04. But i face this problem with my Ubuntu 12.10. Sometime it just boots normally but most of the time it does boot at all. It either stop at the Ubuntu screen or just at the black screen. It is up to date.  

Other two OS boots normally. Please help me on this issue. Thanks

---

### Post by rivode on 2013-01-09
One thing you could try: on the grub boot screen, instead of pressing enter, press "e" (I think) which edits the boot commands, then remove the words "quiet" and "splash".  This will show messages as it boots, which might give you more of an idea about what's going on.

---

