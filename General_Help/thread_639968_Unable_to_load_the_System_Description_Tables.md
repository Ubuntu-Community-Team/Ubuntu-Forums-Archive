---
title: "Unable to load the System Description Tables"
date: 2007-12-13
forum: General Help
---

### Post by PleaseEnjoyThis on 2007-12-13
[ 41.936212] ACPI: Unable to load the System Description Tables
[ 71.398870] Kernel panic - not syncing: No init found. Try passing init: option to kernel.


My computer was down for a few months and I finally got a new motherboard to get it to work (same as my previous mother board.  Now I get this load error when I try to start my computer and when I load from the linux install disc.  I already had grub installed with linux on my hard drive before this.  I haven't been able to find much on this while searching the internet.  Help is loved!

---

### Post by PleaseEnjoyThis on 2007-12-13
!!!

---

### Post by PleaseEnjoyThis on 2007-12-18
!

---

### Post by c-ron on 2008-03-31
I get the same message when passing the kernel the acpi=force parameter from GRUB. My system boots normally (AFAIK) afterwards tho. I can also disable ACPI support by adding acpi=off.

---

