---
title: "module blacklisting on boot"
date: 2008-01-29
forum: General Help
---

### Post by henrique on 2008-01-29
I have a MacBook and have to use the subversion version of madwifi drivers. Last update broke my computer and it cannot boot up. I tried adding noload=ath_pci,... to the grub's kernel command line but it loads the modules.

What can I do?

---

### Post by dcstar on 2008-01-29
> **henrique said:**
> I have a MacBook and have to use the subversion version of madwifi drivers. Last update broke my computer and it cannot boot up. I tried adding noload=ath_pci,... to the grub's kernel command line but it loads the modules.

What can I do?

Try editing this file: /etc/modprobe.d/blacklist

---

### Post by henrique on 2008-01-29
As I said, I cannot boot up, and I was looking for a quicker way than downloading and burning a live cd.

---

