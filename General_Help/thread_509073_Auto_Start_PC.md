---
title: "Auto Start PC"
date: 2007-07-25
forum: General Help
---

### Post by Fragthis on 2007-07-25
Ok here is what I want to do I want my computer to boot up at 9 A.M. every morning My problem my bios does not have a way for me to do that It has a way for me to do it once every day but I want one that boots monday threw friday with out me having to change it every day 

Please help

---

### Post by benx009 on 2007-07-25
sorry, but i don't think this is possible

---

### Post by eentonig on 2007-07-25
Does it support Wake On Lan?

---

### Post by Fragthis on 2007-07-25
I think so but I have wireless

---

### Post by AceofSpades19 on 2007-07-25
I'm pretty sure its impossible to do unless you set it to suspend then its possible

---

### Post by amac777 on 2007-07-25
Perhaps you could set it up to boot everyday using the BIOS, but then have a script that will just immediately shut it back down on the days you don't need it to boot. So the end result would be basically the same.

---

### Post by nniyer on 2007-08-03
without going through the bios - you could possibly try ACPI alarm settings
#cat /proc/acpi/alarm
2007-08-03 10:00:00
// for setting new wakeup time 
# echo 2007-08-03 9:00:00 > /proc/acpi/alarm
// this will autostart the machine at the particular date and time
 
By some basic scripting you could automate this to set next day 9am time when the machine boots up.

hope this helps
-NI

---

