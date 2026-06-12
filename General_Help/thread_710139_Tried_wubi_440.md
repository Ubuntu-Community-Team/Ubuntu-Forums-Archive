---
title: "Tried wubi 440"
date: 2008-02-28
forum: General Help
---

### Post by steve196 on 2008-02-28
(on win2ksp4)
At install after reboot it still plays the startup sound four times.
It tries to set the time without asking for a timezone, unlike normal install, which asks the zone first. The solution would be, to not set the time at all, since Windows has probably done that before.
I had, again, to replace all ro with rw in menu.lst, to avoid a crash because of a write error.

---

### Post by steve196 on 2008-02-28
Installed updates which contained a new kernel. The new kernel does not start. It ends in a shell called BusyBox v1.1.3 with a prompt, that has (initramfs) written in front of it. Normal editing of menu.lst doesn't help.

---

### Post by ago on 2008-02-28
Thanks steve will have a look at both issues. In the meantime feel free to post further info if you find out anything interesting.

---

