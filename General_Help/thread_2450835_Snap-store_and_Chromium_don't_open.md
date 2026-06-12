---
title: "Snap-store and Chromium don't open"
date: 2020-09-22
forum: General Help
---

### Post by jonik2018 on 2020-09-22
I have some problem with snap-store and chromium: after start they  can't open. Gnome-software is working. If run applications in terminal,  in both cases i receive the error

 "Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h:  541: elf_machine_rela_relative: Assertion `ELFW(R_TYPE)  (reloc->r_info) == R_X86_64_RELATIVE' failed!"

 System is update, reboot machine doesn't fix the problem.

---

### Post by jonik2018 on 2020-09-22
Problem is solved: 
[HTML]sudo apt-get --reinstall install snapd chromium-browser[/HTML]

---

