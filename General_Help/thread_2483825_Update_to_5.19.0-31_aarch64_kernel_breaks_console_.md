---
title: "Update to 5.19.0-31 aarch64 kernel breaks console display"
date: 2023-02-09
forum: General Help
---

### Post by perockwell on 2023-02-09
I just applied the latest updates to 22.10 aarch64 running as a VM under VMware Fusion 13 on Apple Silicon. VM was running fine with kernel 5.19.0-29. The updates applied kernel 5.19.0-31. After upgrade, the VM boots, but nothing displays on the VM's console. A ssh session can access the VM, so we know it's running.

Reverting back to kernel 5.19.0-29 returns proper console display.

It's not an isolated incident. Others in the VMware boards are reporting this. Any idea what change in -31 could have caused this?

---

