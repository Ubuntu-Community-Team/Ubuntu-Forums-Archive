---
title: "Running virtual machine crashes desktop"
date: 2007-09-03
forum: General Help
---

### Post by jdogzilla on 2007-09-03
Hello, I have Ubuntu Feisty Fawn with the latest updates, E6400 CPU. SDA1 (the primary drive) is Sata and HDA1 is IDE. 

I initially had Vmware workstation.  If I left the WinXP virtual machine on for more than an hour, the desktop would hang and I would have to reboot.  So I switched over to VMware-server, reinstalled a base version of WinXP with only Symantec Antivirus, and same problem.  I can have the vmware-server software running in the background, but if I start the WinXP VM, it crashes. 

Any suggestions on where I can start looking to diagnose the problem.  I wonder if this is a HDD problem. 

thanks

---

### Post by longlegs on 2007-09-03
try turning off screen saver and power management.
Good Luck
longlegs

---

### Post by gtdaqua on 2007-09-03
i had this problem - culprit was swap. VMWare server would run in the background. After powering up the VM, the machine would become slow and then crash.

reconfigured swap and everything was ok. Type "free" in terminal and see if swap is being utilized. Observe what happens when u run the VM - type "top" in the terminal and see if swap is being utilized.

Ideal size for SWAP is 2x the physical RAM.

---

### Post by jdogzilla on 2007-09-03
Thanks for the suggestions ... I shut the screensaver and disable power mgmt in the Virtual Machine (WinXP) ... still got the same problem.  Swap is never used since all of memory is never used.  

What happens is that the mouse moves, but nothing else responds.  I had top running, and hitting the enter button continuously updated top in a xterm.  No windowed apps would open.  Disk response was extremely slow ... doing an 'ls' in the home directory or in the root directory took forever.  I even tried killing any process that was taking more than 10% of the CPU, but that didn't help.  I had to reboot to restore all original performance.  

Any other suggestions ... what does the module piix do?  Should I also disable the screensaver and power mgmt on the Linux side?  What else can I try?

---

