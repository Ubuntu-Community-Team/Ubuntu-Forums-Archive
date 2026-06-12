---
title: "System thinks it's on battery power"
date: 2005-07-13
forum: General Help
---

### Post by Minilek on 2005-07-13
Hi.  Ubuntu is saying: "System is running on battery power 0 minutes (0%) remaining", but a) the laptop is plugged in, b) the battery is actually full.  Has anyone come across this before?  Also, even though it is saying this, there don't seem to be any bad side effects as a consequence.

---

### Post by varunus on 2005-07-13
What is the output "lsmod"?  What are the contents of "/proc/acpi"?

---

### Post by Minilek on 2005-07-14
ah...after some investigation, I found out acpi was off.  The problem is now fixed -- thanks.

---

