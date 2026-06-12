---
title: "additional parallel port capability"
date: 2007-05-27
forum: General Help
---

### Post by Jensor on 2007-05-27
I already have one parallel port board added giving me a total of three parallel ports. the one on the mother board is at address 0x378, the two on the add-on board are at 0xdff0 and 0xdfa8 and I need two more parallel ports. Is this possible without having address conflicts?

What is the maximum number of parallel ports that may be added?

How do you avoid address conflicts?

Aren't the addresses pre-assigned into the parallel port board?

When you see parallel port boards listed, they never tel lyou what the assigned addresses are untill after you get the board.

Jack Ensor

---

### Post by MoLE on 2007-06-02
I don't see why it wouldn't be possible - if you're using a relatively modern computer with PCI expansion cards for your extra parallel ports, then the motherboard BIOS should sort out the address space issues for you.  This usually happens below the operating system layer, although with older ISA cards, you often had to assign driver parameters so that address conflicts didn't occur.

Out of interest, why do you need 5 parallel ports on one PC?

---

