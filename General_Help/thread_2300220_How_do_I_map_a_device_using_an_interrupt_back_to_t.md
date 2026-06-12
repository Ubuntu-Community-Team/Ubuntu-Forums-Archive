---
title: "How do I map a device using an interrupt back to the bus &amp; port so I can disable it?"
date: 2015-10-24
forum: General Help
---

### Post by KillerKelvUK on 2015-10-24
So I have a usb bus/device operating on interrupt 16 (ehci_hcd:usb5), I'd like to be able to (soft) remove the usb device so as to remove/stop it using the interrupt (temporarily).  I'm likely not using the right words/phrases here for what I'm attempting to describe and carry out so would appreciate someone schooling here...I'm happy to do the research just not clear on what I should be feeding google!

```

cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
  0:         47          0          0          0          0          0          0          0  IR-IO-APIC-edge      timer
  1:          3          0          0          0          0          0          0          0  IR-IO-APIC-edge      i8042
  7:         37          0          0          0          0          0          0          0  IR-IO-APIC-edge    
  8:          1          0          0          0          0          0          0          0  IR-IO-APIC-edge      rtc0
  9:          0          0          0          0          0          0          0          0  IR-IO-APIC-fasteoi   acpi
 12:          4          0          0          0          0          0          0          0  IR-IO-APIC-edge      i8042
 16:         29          0          0          0          0          9          0          0  IR-IO-APIC  16-fasteoi   ehci_hcd:usb5
 18:        826        205        535        663          0        271        518        885  IR-IO-APIC  18-fasteoi   snd_hda_intel
 23:         35          0          0          0          0          0          0          0  IR-IO-APIC  23-fasteoi   ehci_hcd:usb6
 24:          0          0          0          0          0          0          0          0  DMAR_MSI-edge      dmar0
 30:    1154683        132          0       1864   13923431       1408          0      25348  IR-PCI-MSI-edge      xhci_hcd
 31:        344       4351       5125       3542       1474      46273      59715      42054  IR-PCI-MSI-edge      xhci_hcd
 32:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 33:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 34:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 35:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 36:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 37:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 38:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      xhci_hcd
 39:     123508     192872     275198     394850     206545     491244     596899     933290  IR-PCI-MSI-edge      0000:00:1f.2
 40:          0          0          0          0          0          0          0          0  IR-PCI-MSI-edge      p2p1
 41:        926          0          0          0          0    9581571          0          0  IR-PCI-MSI-edge      eth0
 42:         12          0          0          0          0          0          0          0  IR-PCI-MSI-edge      mei_me
 43:        542          0          0          0          0          0          0          0  IR-PCI-MSI-edge      snd_hda_intel
 44:    6147918          0          0          0          0          0          0          0  IR-PCI-MSI-edge      nvidia
 45:    2316334          0          0          0          0          0          0          0  IR-PCI-MSI-edge      vfio-msi[0](0000:07:00.0)
NMI:        967        571        539        552        274        495        268        323   Non-maskable interrupts
LOC:   16507076   13752938   13399083   13878039    5006025    5282888    5107556    5069468   Local timer interrupts
SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
PMI:        967        571        539        552        274        495        268        323   Performance monitoring interrupts
IWI:          3          1          1          0          0          0          1          0   IRQ work interrupts
RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
RES:    1507250    1277769    1214148    1210202    1397583     997624    1424066    1352659   Rescheduling interrupts
CAL:     393232     232644     204702     188736      43440      48767      47451      37491   Function call interrupts
TLB:    1300722     974211     969334     911026     919478     950486     907050     868560   TLB shootdowns
TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
MCP:        803        803        803        803        803        803        803        803   Machine check polls
HYP:          0          0          0          0          0          0          0          0   Hypervisor callback interrupts
ERR:         37
MIS:          0

```

---

