---
title: "IRQ Assignment/Initialization Confusion"
date: 2016-07-09
forum: General Help
---

### Post by senpai2 on 2016-07-09
I am asking a question to better understand what the root cause was.

I have a custom PCI device driver used for memory card operations. I compiled it on Ubuntu 14.04 (linux kernel SMP 3.13.0 low latency) and its basic intended features such as reading/writing and interrupting the device worked fine. 
I upgraded to Ubuntu 16.04 (linux kernel SMP 4.4.0 low latency) and compiled the device driver. Reading and writing worked but interrupts did not work. After digging around I found the IRQ trigger mode and IRQ  number assignment was different between the kernels (/proc/interrupts).

14.04  (linux kernel SMP 3.13.0 low latency) (Working device driver)
IRQ Triggering Mode - IO-APIC-fasteoi
IRQ Assigned Number 18
 
16.04  (linux kernel SMP 4.4.0 low latency) (Not working device driver)
IRQ Triggering Mode - IO-Edge
IRQ Assigned Number 10


After some searching I found this link 
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
I booted the kernel using the flag pci=routeirq 

This fixed the problem and correctly setup the interrupt trigger mode and IRQ number to make the device driver fully functional again.

I want to fully understand what caused the differences in the IRQs. I know the kernel boot flag pci=routeirq tells all PCI device drivers to call pci_enable_device() but I examined the source for the driver and that function is being called.

To the best of my ability after some searching I believe when the machine gets booted the kernel interacts with the MP Table in the BIOS and uses the information there to properly setup the PCI device and perhaps the newer kernel was not reading that correctly. 

If someone has a more through and better idea of what was going on it would be greatly appreciated.

---

