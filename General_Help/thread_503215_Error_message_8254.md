---
title: "Error message 8254"
date: 2007-07-17
forum: General Help
---

### Post by kelimandya on 2007-07-17
First off i would like to say that i am not very experienced at computers, as i am only 15. so any help would be GREATLY appreciated.
 i recently made a Live CD of Ubuntu 7.04 and decided to try and dual boot it along side my current Vista installation.
when i boot from the CD i say "Install" and i get the following error message "[29.4254347]..MP -
Bios Bug: 8254 Timer Not connecred to IO-APIC [29.604286] Kernel Panic - not syncing: IO-Apic + timer doesnt work! Boot with apic = Debug then try booting with the "Noapic" option and send a report."
i have ABSOLUTLEY NO idea what this mean and any help would be GREATLY appreciated.

---

### Post by po0f on 2007-07-17
kelimandya,

When booting the live CD, press F6 (IIRC) at the menu to edit kernel options.  Before the "--" at the end of the kernel boot options, add "noapic", making sure to preserve the space between the new option and the double dash.

---

### Post by kelimandya on 2007-07-17
unfortunatley, the problem is still occuring. any other ideas?

---

