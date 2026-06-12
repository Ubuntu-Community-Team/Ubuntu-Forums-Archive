---
title: "Is there a way to reduce cpu temp with software on linux?"
date: 2005-05-22
forum: General Help
---

### Post by zupermanz on 2005-05-22
Is there a program that cools down the cpu like cpuidle on windows....?

---

### Post by accensi on 2005-05-22
Depends on your processor (cpu). If it supports multiple frequencies, you can use cpufreq, cpudyn or powernowd. All have packages in Ubuntu.

If you AMD Athlon/Duron that cannot change freqs, you can try athcool, and your motherboard is supported, it is also in repositories. apt-cache search or synaptic are your friends!

---

