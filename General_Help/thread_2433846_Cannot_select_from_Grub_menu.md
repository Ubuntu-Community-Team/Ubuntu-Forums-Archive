---
title: "Cannot select from Grub menu"
date: 2019-12-26
forum: General Help
---

### Post by gaston-verhulst on 2019-12-26
Hello,
I have an old i386 computer with Xubuntu and Windows partitions.
Since I have a new Logitech USB keyboard, I cannot move trough the Grub menu items with the down v key in order to select Windows, which comes on the fourth place.
The first one is Xubuntu and will be selected automatically and becomes started and opened and works very well.
On that old i386 computer, I am running Xubuntu 16.04.06.
In the past, Grub was working very well with an old no-USB keyboard, but that doesn't work any more because of water that came in it.
Please, is there a solution in order to solve that Grub problem?
Many thanks in advance for each answer.
Kind regards,
Gaston Verhulst.

---

### Post by oldfred on 2019-12-26
Does your BIOS have a USB setting for USB ports?
Some have full support setting or a special setting for keyboard & mouse use.

First USB keyboards I bought came with adapters to the keyboard & mouse ports.

---

### Post by gaston-verhulst on 2019-12-26
Hello,
First of all, thanks for the quick reply.
With the new USB keyboard, I had an adapter, but it didn't work.

In the BIOS I found:

OnChip USB Controller

USB Legacy Support
- Options
-- Disabled >> is selected
-- No Mice >> I have one
-- All Device

- Port 64/60 Emulation
-- Disabled >> is selected
-- Enabled

Shall I try to change one of the settings?

Thanks in advance,
Gaston Verhulst.

---

### Post by CelticWarrior on 2019-12-26
Yes, I would try enabling Legacy USB support, at least.

---

### Post by gaston-verhulst on 2019-12-26
Hello CelticWarrior,

It runs with your splendid recommendation!
Many thanks, also for the fine communication.

Kind regards,
Gaston Verhulst.

---

### Post by CelticWarrior on 2019-12-26
You're welcome. 

If you consider this solved you can use the thread tools to mark it as solved.

---

