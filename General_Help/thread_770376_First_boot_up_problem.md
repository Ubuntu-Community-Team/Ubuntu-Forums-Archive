---
title: "First boot up problem"
date: 2008-04-27
forum: General Help
---

### Post by ubockto on 2008-04-27
I am having problems booting up, all it is doing is the scroll bar is stuck at the begining, I have tried editing to include "acpi=false", but this doesnt help

---

### Post by ryanhaigh on 2008-04-27
Using the same way you edited the line to add acpi=false you can remove quite and splash so that you can see the boot process text and hopefully determine the point at which it gets stuck.

---

### Post by ubockto on 2008-04-27
Ok, I have solved it, first of all the command is not suppose to be false, but off, and now have turned off the acpi support on my bios, and now seems to be working fine, thanks:popcorn::KS

---

