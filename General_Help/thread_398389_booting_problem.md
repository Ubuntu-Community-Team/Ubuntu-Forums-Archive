---
title: "booting problem"
date: 2007-03-31
forum: General Help
---

### Post by matiw on 2007-03-31
hi everyone

i have this annoying problem.... when i try to open ubuntu from the livecd this error message appears:

[17179570.884000] Kernel panic - not syncing: IO-APIC +timer doesn't work! boot with apic=debug and send a report. Then try booting with the 'noapic' option [17179570.884000]

well, i use the noapic option, but i would like to fix this problem, cause it's not only ubuntu it happens with other distros.

---

### Post by acormack on 2007-04-01
APIC = Advanced Programmable Interrupt Controller 

see  [http://www.vmware.com/community/thread.jspa;jsessionid=BBC1B2730E122E01A5A00ABBCDC41CF9?messageID=92797&#92797](http://www.vmware.com/community/thread.jspa;jsessionid=BBC1B2730E122E01A5A00ABBCDC41CF9?messageID=92797&#92797) for discussions

running with noapic permanently would not be optimal - but if you only need the noapic option to get the OS installed I would not worry.

You could try playing around in your bios for settings relating to PCI / interrupt settings if you want  this to go away completely.

Always document what you change though.

---

