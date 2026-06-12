---
title: "After upgrading to 13.10 Saucy Salamander, I end up at the initramfs prompt"
date: 2013-12-10
forum: General Help
---

### Post by supradave2 on 2013-12-10
I'm having a small problem with one of my machines.  When I reboot after the upgrade to 13.10, I end up at the initramfs prompt.  If I do an ```
ls /dev/mapper
```, I have nothing.  If I wait a minute or two and do it again, it starts populating with drives.  I can then type exit and the machine boots and works fine.  Not quite certain how even to start debugging this problem.

In grub, my default linux kernel is:
```
linux    /vmlinuz-3.11.0-12-generic root=/dev/mapper/ubuntu--vg-root ro   quiet splash $vt_handoff
initrd    /initrd.img-3.11.0-12-generic
```

---

