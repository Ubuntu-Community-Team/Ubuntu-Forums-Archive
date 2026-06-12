---
title: "Printer - CUPS holding all jobs on all printers"
date: 2014-07-17
forum: General Help
---

### Post by swilsonz on 2014-07-17
OS version 14.04

Suddenly all my print jobs to all printers have to be released manually.  I prefer to print without the extra step.

I have checked the GUI for each printer (properties/job options/common options/more/hold until) and it is set to "No Hold".

I have also checked [COLOR=#000000]/etc/cups/printers.conf and there are no hold option set there:

[/COLOR]<DefaultPrinter ##################>
UUID urn:uuid:9df21165-70d6-3f4d-5fac-46d1d2416e04
Info ###########################
Location ###############
DeviceURI hp:/net/hp_LaserJet_4200?ip=999.999.999.999
PPDTimeStamp *
State Idle
StateTime 1405614463
Type 8425684
Accepting Yes
Shared Yes
ColorManaged Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option media-col media-bottom-margin
Option orientation-requested 6
</Printer>
<Printer ===================>
UUID urn:uuid:8967583b-6bdd-3943-64ba-3a53a7cade34
Info =======================
Location =============
DeviceURI dnssd://RICOH%20Aficio%20MP%204001._pdl-datastream._tcp.local/
PPDTimeStamp *
State Idle
StateTime 1405614526
Type 8433908
Accepting Yes
Shared Yes
ColorManaged Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option media-col media-bottom-margin
Attribute marker-colors \#000000,#000000
Attribute marker-levels -1,-1
Attribute marker-names Toner,Waste Toner
Attribute marker-types toner,waste-toner
Attribute marker-change-time 1405614526
</Printer>

---

### Post by tgalati4 on 2014-07-17
Open a terminal:

```
lpstat -a
```

Check your log files:

```
cat /var/log/cups/error_log
cat /var/log/cups/access_log
cat /var/log/cups/page_log
```

---

