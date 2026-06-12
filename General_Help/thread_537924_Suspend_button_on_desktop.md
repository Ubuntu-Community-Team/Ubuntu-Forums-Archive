---
title: "Suspend button on desktop"
date: 2007-08-29
forum: General Help
---

### Post by k17s0s on 2007-08-29
Hi, I'm using kubuntu feisty on a desktop pc, and i want to suspend it to ram, but this button is absent from the log out options... (there's log out, hibernate, restart and shut down)
How can i enable it?

---

### Post by k17s0s on 2007-09-02
No ideas? :(
could it be that it's not supported for my motherboard?
```
cat /sys/power/state
``` gives
```
standby disk
```
and
```
cat /proc/acpi/sleep
``` gives
```
S0 S1 S4 S5
```

---

