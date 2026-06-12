---
title: "How do I load a module so that it will get its own interrupt??"
date: 2007-10-29
forum: General Help
---

### Post by netstv on 2007-10-29
I am running an Asterisks server that handles SIP and POTS calls.  The way it does POTS is over a T1 line using a Rhino T1/E1 card.   I get very bad static on the line and I believe the issue is that the Rhino module (rxt1) is sharing interrupts with the ethernet card.

[FONT="Fixedsys"] 

cat /proc/interrupts 
           CPU0       
  0:   62275792    XT-PIC-XT        timer
  1:       2228    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  7:          0    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:          0    XT-PIC-XT        acpi
 10:      22486    XT-PIC-XT        uhci_hcd:usb1, CS46XX
 11:  251107999    XT-PIC-XT        eth0, rxt1
 14:      79384    XT-PIC-XT        ide0
 15:    2234231    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0[/FONT]

You'll notice that rxt1 at interrupt 11 is shard with eth0.  I am not sure why it's sharing that interrupt.  I have tons left.  

Anyway, thanks for any help.

-netstv

---

### Post by #Reistlehr- on 2007-10-29
No idea, but this could come into handy for myself one day too, so bump.

---

