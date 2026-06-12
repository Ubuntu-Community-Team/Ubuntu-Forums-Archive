---
title: "I need help with Ubuntu.."
date: 2008-06-25
forum: General Help
---

### Post by rofl copter on 2008-06-25
Someone on my forums site said that for Linux, i should go to wubi-installer.org and install ubuntu from there. So I did. When I restart my pc, it asks if I would like to run it in either Windows Vista or Ubuntu. I select Ubuntu, and then it says press ESC for menu, I just skip that, and it loads, then this pops up:
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
What do I do?

---

### Post by rofl copter on 2008-06-25
Please help?

---

### Post by mempman on 2008-06-26
> **rofl copter said:**
> Someone on my forums site said that for Linux, i should go to wubi-installer.org and install ubuntu from there. So I did. When I restart my pc, it asks if I would like to run it in either Windows Vista or Ubuntu. I select Ubuntu, and then it says press ESC for menu, I just skip that, and it loads, then this pops up:
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
What do I do?

I'm not familiar with wubi, but to boot into ubuntu, you need 2 things...1) kernel location 2) initramfs module.  I would guess that you are missing the kernel and are landing on initramfs prompt and that is why your boot is failing.

What happens when yo uhit the ESC key, as you indicated above, try it!

---

