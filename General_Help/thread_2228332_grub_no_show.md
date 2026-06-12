---
title: "grub no show"
date: 2014-06-06
forum: General Help
---

### Post by Pedroski55 on 2014-06-06
Hi, I just installed 14.04 on my old laptop using a new harddrive. Ubuntu is the only system. When I boot, I do not see any grub boot screen, or any choices, like I normally do on my other computers. I see a black screen, but no text.  Is there something wrong, or is this normal behaviour when there is only one system??

---

### Post by oldfred on 2014-06-06
If you just have one system, it knows to boot that. 
If you need menu for boot parameter,  recovery,  or to boot old kernel, you can hold shift key from BIOS until menu appears.

---

### Post by Pedroski55 on 2014-06-07
I changed grub.cfg timeout = 0 to timeout = 30 now I can see the grub screen ok.

---

