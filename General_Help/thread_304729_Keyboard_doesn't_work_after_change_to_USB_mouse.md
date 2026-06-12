---
title: "Keyboard doesn't work after change to USB mouse"
date: 2006-11-22
forum: General Help
---

### Post by rogblake on 2006-11-22
I'm running Ubuntu Dapper on a system that dual-boots with MS Windows. (Under normal circumstances the latter is rarely, if ever, used.)

I had been using PS/2-type mouse and keyboard on this system, but the PS/2 mouse port on the motherboard just stopped working (no PS/2 mouse would work in either Dapper or Windoze), so a USB mouse was connected instead.  Dapper picked up the mouse automagically with no problem, but now my PS/2 keyboard has stopped working! The keyboard and USB mouse both work fine on the Windows side of the system so I know it's not a hardware problem.

Anyone know the proper mystical incantations needed to get the PS/2 keyboard working in conjunction with the USB mouse? (I'm pretty much stuck using Windoze on this system until this problem is sorted out -- in fact that's what I'm using now to type this message. Help!!!)

---

### Post by rogblake on 2006-11-26
Looks like it (probably) was a hardware problem after all, one that was affecting different software in different ways. Through testing I found that the keyboard would work in Windoze, the BIOS setup, and bootloaders, but not with the Linux 2.6 kernels -- newer Linux boot CDs would not work, but older CDs based on the 2.4 kernel worked OK.

I "fixed" the problem by installing a PS/2 to USB adapter for the keyboard to make an end-run around the apparently flakey PS/2 hardware on the motherboard. (Of course I could have just bought a USB keyboard, but I much prefer the original, high-quality IBM PS/2 keyboard I'm using over today's cheap Chinese units.)

---

