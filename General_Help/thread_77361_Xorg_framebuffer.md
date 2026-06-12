---
title: "Xorg framebuffer"
date: 2005-10-16
forum: General Help
---

### Post by codon on 2005-10-16
Hi,

I have noticed that when I enable the framebuffer via the kernel option vga=xxx, the performance of X decreases substantially, making HD videos unplayable.  Without the framebuffer, X performance is fine.

Is there a way to instruct X.org to ignore the framebuffer, even if it is present?  I would like to keep my boot splash but still have acceptable performance playing video using xv.

I have tried the option "UseFBDev" "false", but that option is not supported by my driver, i810.

Thanks

---

### Post by codon on 2005-10-16
I can confirm that it is vesafb that is causing this problem.  If I boot with the standard usplash (append "splash" to kernel), my performance is good.

This problem only occurs when I pass in vga=xxx.  Xorg performance tanks when playing video using xv.

---

