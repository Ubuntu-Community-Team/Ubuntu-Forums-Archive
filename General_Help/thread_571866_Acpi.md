---
title: "Acpi"
date: 2007-10-09
forum: General Help
---

### Post by BigBishop on 2007-10-09
Hi All,

I think i found a way to get my board to boot but i need to turn off ACPI.  How do i do this.  Im not in front of my computer right now so i cannot check to see if it is a BIOS setting but from the posts i have read it looks like it is a GRUB setting.

Anyone?

---

### Post by geraldm on 2007-10-10
acpi=off

I have seen posts that add the above to the kernel  line in the file
/boot/grub/menu.lst  

Back up the file before editing it. 

Gerald

---

