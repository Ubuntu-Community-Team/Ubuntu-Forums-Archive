---
title: "Kernel Panic on X31"
date: 2008-07-08
forum: General Help
---

### Post by bobbarker on 2008-07-08
Maybe this should be over in the laptop section...we'll see.

My X31 crashes frequently, every 5-20 minutes. It's entirely random and I haven't a clue why. It's a BSOD in XP and a Kernel Panic in ubuntu. Here's what I get:
```

PANIC: double fault, gdt at c1204000 [255 bytes]
double fault, tss at c1207100
eip = c03190f9, esp = ce83bfc4
eax = ce83c010, ebx = 00000001, ecx = 0000007b, edx = 00000000
esi = 00030001, edi = ce83c010

```
I'm using 8.04 (fresh install) on a 1.6ghz Thinkpad X31.

I know it's not overheating because I've checked temps through acpi and they're fine and I've checked the heat sinks, they're fine too. The hard drive is only 6 months old (no problems until now) and the ram has all passed several loops of memtest. I've even cleaned out the system carefully with a can of air.

On an odd note: the system seems to 'stay up' longer if I'm in CLI rather than Gnome.

---

