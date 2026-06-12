---
title: "Simple Question: system logs out automatically and programs got killed"
date: 2007-02-14
forum: General Help
---

### Post by xingerguan on 2007-02-14
My system will log out automatically after some time I don't use it, and all the programs are killed.
How can I control (set up) the time for lock and do NOT kill my programs?
I tried system -> preferences -> power management, but looks it's not the one.

---

### Post by jimbob on 2007-02-15
Try adding acpi=off and noapic parameters to the kernel line in your grub bootup sequence.

ACPI = Advanced Configuration and Power Interface

APIC = Advanced Programmable Interrupt Controllers

ACPI is the system that controls your dynamic speed fans, the power button behavior, sleep states, ect.

APIC is the replacement for the old PIC chip that used to come imbedded on motherboards that allowed you to setup interrupts for your soundcard, ide controllers, ect.

In general I'd leave the APIC settings alone. It has been some time since I've had a problem related to that.

However, many computers ship with buggy or out of spec. ACPI firmware which can cause any number of wackiness. If you are noticing your machine randomly powering off or failing to boot disabling this often helps
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by ckoester on 2007-05-05
I'm having the same problem and I believe that the screensaver is crashing X.  When the screensaver starts it automatically logs me out.

If I try to change the screensaver settings it abruptly crashes X.  I have not found a fix for this yet.

---

