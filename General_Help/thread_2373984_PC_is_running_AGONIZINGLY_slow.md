---
title: "PC is running AGONIZINGLY slow"
date: 2017-10-11
forum: General Help
---

### Post by Evil Wayz on 2017-10-11
I bought a new dell pc,and put 17.04 on it.  It was working fine and then the power supply went bad, so they company replaced it.  Now, its running incredibly slowly.  I can type a sentence, and it will take to the count of ten to show up on the screen.  Same with the mouse, I have to hover over what I want to click for sometimes as much as ten seconds before it will turn from the arrow to the selection finger.  Also theres only 24 gb of space left on the drive out of19. 

I was wondering if this was a software problem or a hardware problem. 

Ubuntu 17.04 with xubuntu desktop and current kernel

---

### Post by timbofield on 2017-10-11
I just had this, I think something is up with the latest kernel.  Restart your PC, hold down escape, and select the previous kernel. That fixed it for me for now.

---

### Post by Evil Wayz on 2017-10-11
That did it.  How do we let the good folks who write the kernel know about this?

---

### Post by Doug S on 2017-10-11
please give the kernel versions (uname -a) that work and do not work.
Questions: Did the kernel that doesn't work get loaded at a similar time to when the power supply was changed? And is it a Dell power supply? Reason for asking: Dell uses something in their power supplies to identify them as Dell, and if not they enable clock modulation which (unless your kernel is very new) would cause a very very slow system with the intel-pstate CPU frequency scaling driver

---

### Post by Evil Wayz on 2017-10-11
4.10.0-35-generic
Is the last kernel that works without the weird slow down.  

As far as I know they sent a Dell power supply.  And according to additional drivers I'm using the microcode.

---

