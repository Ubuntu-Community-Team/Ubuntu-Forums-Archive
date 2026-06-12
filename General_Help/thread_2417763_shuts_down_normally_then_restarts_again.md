---
title: "shuts down normally then restarts again"
date: 2019-04-26
forum: General Help
---

### Post by Searlec on 2019-04-26
Current level 18.04.2
system shuts down normally from off switch on desk top ( either direct or delayed) then performs an unwanted boot.
System suspension works properly
System shuts then reboots if normal off is pressed on box front
System shuts down the reboots (unwanted) when shut down from terminal "shutdown -P now"
Not sure how to approach. 
Fresh Install?

---

### Post by rbmorse on 2019-04-27
I have a Windows 10 machine that does this.  It's an older Intel branded DZ77 motherboard.  We tracked the problem to an ACPI issue in the BIOS.  Filed a bug report, got a nice reply from Intel saying the issue had been previously noted and would be addressed in a subsequent BIOS update...which never got released. 

I would suggest you go through your BIOS/UEFI settings and verify everything relating to ACPI and power management.  Disable all settings that wake the system from anything other than the power button (things like "wake on LAN", "wake timer" "wake on mouse or keyboard". etc) and see if that helps.

---

### Post by Searlec on 2019-04-28
Thanks , your analysis rings true. Will undertake one change at a time. Meanwhile I have found a workaround so I can trouble shoot with deliberation. This is an Intel DH87RL motherboard of some vintage. The condition appeared quite suddenly right after the latest kernel update which may have exposed a heretofore unaffected setting.

---

### Post by Searlec on 2019-04-29
Thank you rbmorse. Culprit was either  "wake on Lan from S4/S5 " and/or "PCIe ASPM support. Both now disabled in their own way. All appears well.

---

### Post by Searlec on 2019-04-29
Restored PCLe - Problem was "wake on LAN'---- now disabled. Would like to close - don't know how

---

