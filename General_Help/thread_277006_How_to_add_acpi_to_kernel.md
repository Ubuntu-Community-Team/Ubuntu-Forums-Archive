---
title: "How to add acpi to kernel"
date: 2006-10-13
forum: General Help
---

### Post by hcjc92 on 2006-10-13
I have server edition w/ fluxbox, and i need to add acpi/apm to the kernel, i'm have NO idea how to do this, help please :)

---

### Post by PriceChild on 2006-10-13
I thought acpi was built into the kernel?

Many users of laptops especially have problems without turning this off at boot.

Could you explain the reason why you believe you need it?

---

### Post by hcjc92 on 2006-10-13
Because i have 3 different battery monitors, and they all complain of not having acpi support in the kernel :D and i need a batter monitor

---

### Post by doobit on 2006-10-13
acpi is built into the kernel. If you want a manager us synaptic to get acpi and apmd. or apt-get install apmd
Another good monitor is Conky

---

### Post by hcjc92 on 2006-10-13
Okay, both acpi and apmd are installed and uptodate but that still doens't explain why xbattbar, wmbattery and the other thing i have have issues with acpi and or apm :D lol the other was gkrellm btw

---

### Post by doobit on 2006-10-13
On some systems you have to force them. I put apci=force in the linux boot command line of GRUB. Maybe you need to do that too.

---

### Post by hcjc92 on 2006-10-13
hmpf :| i just did that, and it still won't work, is there anyway to see if acpi is working?

---

### Post by hcjc92 on 2006-10-14
Well, how would i add acpi to the kernel if it wasn't there?

---

