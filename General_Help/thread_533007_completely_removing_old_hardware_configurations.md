---
title: "completely removing old hardware configurations"
date: 2007-08-23
forum: General Help
---

### Post by miatawnt2b on 2007-08-23
I have swapped out a motherboard on an ubuntu box, but used the same PCI video capture cards.  It seems that ubuntu sees these cards as different hardware devices than it did before.  I am assuming this is because it never deleted old device configurations. Where can I tweak this stuff?
-J

---

### Post by MoLE on 2007-09-02
My understanding is that the kernel will detect at each and every boot, which hardware is required.  modprobe is the tool that works out which kernel module to load, and I think there is a spot for configuring this in /etc/modprobe.d/* from memery, although I'd probably read the modprobe man pages first to check.

Can you do lspci -vvv and lsmod and post the results?

---

