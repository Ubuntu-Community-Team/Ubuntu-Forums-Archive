---
title: "uninstalling CUPS?"
date: 2008-05-15
forum: General Help
---

### Post by albert1234 on 2008-05-15
I want to uninstall CUPS, because it does not work with my hardy(guest) system in VMWare.
Could somebody tell me which packets are invoved? (I would like to use turboprint instead)

---

### Post by chrisccoulson on 2008-05-15
Someone please correct me if I'm wrong, but I'm sure you still need CUPS in place when using the Turboprint drivers

---

### Post by brian_p on 2008-05-15
> **chrisccoulson said:**
> Someone please correct me if I'm wrong, but I'm sure you still need CUPS in place when using the Turboprint drivers

More an expansion than a correction: turboprint needs cups or lprng as a spooler.

---

### Post by chrisccoulson on 2008-05-15
Thankyou, I thought it might have some sort of dependency

---

### Post by albert1234 on 2008-05-15
I think, I have a lot of bugs in my CUPS. So I  uninstalled and subsequently installed CUPS again. But no change. Though cupsserver is running I cannot print

While uninstalling and reinstalling CUPS the printers.conf file has obviously not changed. This might be a problem. For further investigation here is the file content:
<Printer PDF>
Info PDF
DeviceURI cups-pdf:/
State Idle
StateTime 1208886882
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
# Beginning of the block added by the VMware software
<Printer VMware_Virtual_Printer>
   Info VMware_Virtual_Printer
   DeviceURI tpvmlp://VMware1
   State Idle
   Accepting Yes
</Printer>
# End of the block added by the VMware software

By the way my printer is on LPT1. I can print a testfile with Turboprint. But I cannot print out of a program (cups scheduler is not running a.s.f.) Perhaps one of you can post his conf-file preferably if he has his printer on LPT1

---

