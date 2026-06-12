---
title: "[EDGY] Boot is very long"
date: 2006-10-29
forum: General Help
---

### Post by kal on 2006-10-29
Hello everybody,

I've just installed Edgy and i have some troubles when my laptop boot. Indeed, it "freeze" at

```
Running /scripts/local-top
```

During 3 minutes, then continue.

If i try to boot in recovery mode, it freeze at :

```

Begin: Running /scripts/local-top...
...
[17179581.992000] ACPI: PCI Interrupt 0000:00:1f.2B -> GSI 18 (level, low) -> IRQ 201

```

Is there a workaround for that problem/bug ? ](*,)

---

### Post by kal on 2006-10-29
Calling the kernel with 

> nolapic noapic acpi=off

solved the problem.

---

