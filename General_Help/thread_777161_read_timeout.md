---
title: "read timeout"
date: 2008-05-01
forum: General Help
---

### Post by eisenklopf on 2008-05-01
okay so did a fresh install in  order to get 8.04 on and every time i try to boot into it i get this...

[   23.927646] ACPI: EC: acpi_ec_wait timeout, status=0, expect_event=1
[   23.927704] ACPI: EC: read timeout, command=128

now the numbers change all the time but the rest remains the same. So any ideas?

---

### Post by Monicker on 2008-05-01
This might help.  It suggests using the "acpi=off" parameter during boot, and has a link to instructions for doing that:

[https://bugs.launchpad.net/ubuntu/+bug/222864]("https://bugs.launchpad.net/ubuntu/+bug/222864")

---

### Post by eisenklopf on 2008-05-02
thank you. seems to be a sony bug as I am running a VGN-AR390E and all others I seen reported are Sonys.

---

### Post by bekirserifoglu on 2008-05-25
i have a vaio fz190 and i can confirm that i have the same problem. however, it doesn't always occur. i compiled the latest kernel myself and the problem seems to be gone.

---

### Post by bekirserifoglu on 2008-05-29
check this out

[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137[/HTML]

---

### Post by jonathanpeter on 2008-05-31
Another solution is to disable the boot flash screen.  (I also have a sony).

---

