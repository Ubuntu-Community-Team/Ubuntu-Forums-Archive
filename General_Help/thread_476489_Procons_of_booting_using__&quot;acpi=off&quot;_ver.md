---
title: "Pro/cons of booting using  &quot;acpi=off&quot; versus &quot;noapictimer&quot;?"
date: 2007-06-17
forum: General Help
---

### Post by chefele on 2007-06-17
I just bought a new eMachines T-series T3612 & installed Ubuntu 7.04 on it.     I found I could only get it to boot with two sets of kernel boot parameters in GRUB:   "acpi=off irqpoll"  or "noapictimer irqpoll".  I need advice on which of these two sets of parameters is best.

Without any additional parameters, 7.04 (& 6.10 & 6.06LTS) would boot and run *extremely* slowly.   Once booted, the "top" command showed that kacpid & kacpi_notify processes were using up 99%+ of CPU.  There were ACPI exception messages in the "dmesg" command output:

[   55.967087] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   55.967209] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   55.967322] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]

So I went into GRUB & edited the boot parameter list to add "acpi=off irqpoll".  That worked!  The system then booted normally & quickly. 
But further tinkering *also*  showed that adding, "noapictimer irqpoll"   worked as well.  (A complete list of parameters that did *not* work is at the end of this post, if that helps)   

So, my question is, which set of parameters is "better" and/or  makes me lose the least functionality?     What are the pros/cons of using  "acpi=off irqpoll"  vs  "noapictimer irqpoll" ??? 

I understand that since ACPI is for power/fan management.  So I'd lose sleep/power-down functions by turning it off.    BUT  if I turn ACPI off, what would  control the fan speed / cooling functions? (basically, I don't want my processor to overheat)

On the other hand, what would I lose if I turned off the APIC timer using "noapictimer"? 
I've only seen "noapictimer" mentioned in reference to AMD processors & system clocks that run at double-speed.  But my  system uses an Intel Celeron D, and the clock seems to run fine.
But the "dmesg" command shows a stream of errors like this:

   [10263.247596] APIC error on CPU0: 40(40)
   [10263.251593] APIC error on CPU0: 40(40)
   [10263.255592] APIC error on CPU0: 40(40)
   [10263.259610] APIC error on CPU0: 40(40)

Should I be concerned? 

I'm new to this type of configuration (& this forum), so any tips would be appreciated.

 *** UPDATE ***  
          I settled on using ACPI=off irqpoll.   
          The BIOS seems to take care of adjusting the fans OK,
          but I can't read processor temps & I have to manually turn off the PC. 
          But this is OK, since this isn't my main machine.

*** UPDATE #2 ***
          I recently upgraded to 7.10, and the system hangs during shutdown as well.
          To fix it, I added the following line: "apm power_off=1"   to  the end of /etc/modules
          Now my machine shuts off cleanly on its own.  


PS 
For completeness, here's the set of GRUB kernel-boot parameters that I added that did NOT work (i.e. very very slow system):

noapic nolapic irqpoll
noapic irqpoll
nolapic irqpoll
apic=off irqpoll
acpi=noirq irqpoll
noapic
pci=routeirq
pci=noacpi
apic=off
nolapic
noacpi
irqpoll
acpi=noirq
noapic acpi=noirq
noapictimer
noapic acpi=noirq nolapic
noapic nolapic
pci=biosirq
pci=biosirq irqpoll
noapic irqpoll

Additionally, the following two sets of parameters worked, 
but I had no Ethernet / Internet access (adding irqpoll fixed this):

acpi=off
noapic acpi=off

---

### Post by duhblow7 on 2007-07-12
thanks for this post.  it is very informative and helped me out a lot.  it wasn't in vain!

---

### Post by chefele on 2007-08-03
Thanks, glad to help!  

If anyone else has any good/bad experiences getting Ubuntu to run on the eMachines T3612, please share them.

---

