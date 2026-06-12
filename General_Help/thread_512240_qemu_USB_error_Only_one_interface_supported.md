---
title: "qemu USB error: Only one interface supported"
date: 2007-07-28
forum: General Help
---

### Post by Zeroedout on 2007-07-28
Hello, I recently installed qemu and windows XP in ubuntu in order to sync my phone (Nokia 9500 communicator, which has horrid linux support since Nokia has proprietary, non-standard everything on this phone). Unfortunatly, when I add the usb device, it says it's unable to add it, only one interface supported. I'm pretty sure permissions are okay (sudo chown -R 1000 /proc/bus/usb  when I do not do this, it gives the obvious permission denied error). I saw a patch in the qemu faq, however the link was dead. Does anyone know how I can list/select the interface? Or even if you have a link to the patch for the current version, compiling it is okay with me, however since I have very limited net access, a last resort.

---

### Post by Zeroedout on 2007-08-05
Has anyone had any usb device work that has multiple interfaces?

---

### Post by wina on 2007-08-18
hi,

there is a patch for this issue.

[this]("http://stud4.tuwien.ac.at/~e0425650/html/linux-qemu.html") might help you out
[http://stud4.tuwien.ac.at/~e0425650/html/linux-qemu.html]("http://stud4.tuwien.ac.at/~e0425650/html/linux-qemu.html")

bye,
Andi

---

