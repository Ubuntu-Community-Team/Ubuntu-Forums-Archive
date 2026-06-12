---
title: "Kernel Panic"
date: 2007-09-15
forum: General Help
---

### Post by jamestrowbridge on 2007-09-15
My kernel on feisty panics within about 5 minutes after boot.  Can someone tell me what I will need to post about my system to find the reason why?  Thank you....also if you would rather email: [email]jamestrowbridge@gmail.com[/email]

---

### Post by kevstar31 on 2007-09-16
I need to know the make and model of your computer.

---

### Post by RedSquirrel on 2007-09-17
I would start by running the memory test from the grub menu to see if your memory is OK.

---

### Post by jamestrowbridge on 2007-09-27
I have a Pentium III 1.3Ghz 768MB RAM I'm using an AGP ATI Radeon 9200se graphics card Dvd-RW & a CDROM drive, 2 HDD IDE....anything else...let me know.

---

### Post by jamestrowbridge on 2007-09-27
I may have fixed it...like I have before- I used: 
irqpoll noapic nolapic pci=irqroute pci=noacpi acpi=off framebuffer=false
all after the kernel line in grub (and made it permenant in menu.lst)
I used this before and forgot what I did exactly, but it's working so far...I'll let you know if it starts doing it again.  Thanks.

---

