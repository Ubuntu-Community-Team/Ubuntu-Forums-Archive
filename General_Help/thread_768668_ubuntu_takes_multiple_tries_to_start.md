---
title: "ubuntu takes multiple tries to start"
date: 2008-04-26
forum: General Help
---

### Post by Heavy Light 117 on 2008-04-26
XP starts fine from grub but ubuntu gets stuck right after grub. Usually it takes a couple restarts. What gives?

---

### Post by phonkenstein on 2008-04-26
I've been having the same problem for quite a while now and haven't found a solution.

---

### Post by firecat53 on 2008-04-26
Depending your hardware, you may have add some entries to your /boot/grub/menu.lst ubuntu entry.

For example, I have an hp dv6000 and I usually have to add 'noapic irqfixup' to the kernel line to get everything working correctly and booting normally.

kernel          /vmlinuz-2.6.22-14-generic root=UUID=8bd7824a-6203-4050-a3fb-ac5812bba159 ro quiet splash noapic irqfixup


Google around for your hardware and see if other people have had the same problem. Could be any combination of noapci, noacpi, acpi=off, irqfixup, or one of many other boot parameters.

Good luck!
Scott

---

### Post by Heavy Light 117 on 2008-04-26
> **firecat53 said:**
> Depending your hardware, you may have add some entries to your /boot/grub/menu.lst ubuntu entry.

For example, I have an hp dv6000 and I usually have to add 'noapic irqfixup' to the kernel line to get everything working correctly and booting normally.

kernel          /vmlinuz-2.6.22-14-generic root=UUID=8bd7824a-6203-4050-a3fb-ac5812bba159 ro quiet splash noapic irqfixup


Google around for your hardware and see if other people have had the same problem. Could be any combination of noapci, noacpi, acpi=off, irqfixup, or one of many other boot parameters.

Good luck!
Scott

My computer is acting weird left and right. I think it might just be a ram problem. Thanks for the help.

---

