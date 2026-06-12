---
title: "Boot halts on Ibm R40"
date: 2005-04-08
forum: General Help
---

### Post by Grul on 2005-04-08
I tried out the Ubuntu Live CD, the latest version from the Ubuntu homepage. However, the boot comes to the point where these lines are printed:

ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU] (supports 8 throttling states)

Then nothing happens. This is on an IBM R40e laptop. I've tried some boot options like the one that says "enable for some R40 laptops", with no discernible difference.

I am interested to install Ubuntu on my laptop since it seems to be a good distribution, but I wonder if it is any point if even the Live CD doesn't work?

---

### Post by mendicant on 2005-04-08
You can try appending various options, like "noapic pnpbios=off acpi=off"
and combinations of those.

---

