---
title: "ubuntu install error"
date: 2007-10-31
forum: General Help
---

### Post by luckycharmz68 on 2007-10-31
Help, I am getting timer does not work msg, along with noapic error when trying to start and or install ubuntu, anyone have any ideas i would appreciate the info. thanks.

---

### Post by luckycharmz68 on 2007-10-31
this is a pic of the error

---

### Post by xyphur on 2007-10-31
after plugging "8254 timer not connected to io-apic" into Google, the first result linked back to these forums. The fix that two people have verified to work is during install is to add 'noapic' to the boot line on the install CD.

Press F6 when you have the CD menu upon bootup, and add 'noapic' right before the last two hyphens (without the quotes)... should solve the timer issue...

Also, depending on your motherboard/BIOS there may be an option to disable IOAPIC altogether, which should also solve this issue. Apparently, this is a known issue with nForce chipsets, as far as I've read anyway.

---

### Post by xyphur on 2007-10-31
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355) was the thread I located this in, btw...

---

