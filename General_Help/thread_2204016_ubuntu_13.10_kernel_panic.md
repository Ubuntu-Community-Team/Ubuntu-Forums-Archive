---
title: "ubuntu 13.10 kernel panic"
date: 2014-02-06
forum: General Help
---

### Post by camsarria-k on 2014-02-06
Good evening, i am plagued by this issue

Whenever i update ubuntu to the latest kernel (presently using 3.13.0-031300-generic) with the latest amd proprietary drivers (using latest beta compatible with the kernel), the system runs very well, and way better then with the original kernel that comes with ubuntu.

However every time i start the computer for the first time after shutting it down for a long time, i always get a kernel panic, everything closes and when i use control T and try to do anything the keyboard starts flashing and the system freezes, after this i reboot and nothing more happens and the system runs smooth the rest of the day usage - if i reboot the system works fine after; if i shut the computer down and return later i get the kernel panic on the first boot, reboot and everything works fine.

This only happens if i update the kernel that is bundled with ubuntu.

Anyone has had this issue? if so, what can i do to resolve it? its not a showstopper issue but can be annoying.

Best regards

Carlos

---

### Post by grier-devon on 2014-02-06
From my understanding a "Kernel Panic" is either a bug in the kernel or software causing the issue, the problem is  finding the source of the crash since the kernel crashed there shouldn't be any logs on it or any that could be trusted. The only thing I can think of is the kernel/CrashdumpRecipe, it looks a little outdated but should still work.

[https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe)

---

