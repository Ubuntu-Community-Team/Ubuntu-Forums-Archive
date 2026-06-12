---
title: "LiveCD boot. X starts, gnome freezes."
date: 2006-11-03
forum: General Help
---

### Post by Nirro on 2006-11-03
Hello, 

I try to start the LiveCD (Edgy) on a friend's computer.

X starts. When the startup music theme starts to play the computer get stuck, and the first note of the theme is repeated again and again.

Is anyone familiar with that problem ?
I can move to terminal (by pressing ctrl+alt+F1). What can I do to analyze or fix the problem ?


Thanks.

---

### Post by john_spiral on 2006-11-03
How old is your system, what type is it?

---

### Post by Nirro on 2006-11-03
It is AMD AthlonXP 1800+.
Motherboard is from Gigabyte.
What else do you need ?

In the past I could run Debian and SUSE on this system.

---

### Post by thekingof7 on 2006-11-03
Well Edgy is still in the development stage is it not? SO why dont you try Dapper?

---

### Post by Nirro on 2006-11-03
No. Edgy is stable.

---

### Post by Nirro on 2006-11-03
The problem was solved by adding the bootup settings : 
noapic nolapic acpi=off


Thanks.

---

