---
title: "Cannot share a printer with cups..."
date: 2006-10-22
forum: General Help
---

### Post by dierre on 2006-10-22
Hello

I have a small home network with an ubuntu 5.10 sharing a printer, a hp deskjet 950C.

With a windows client the sharing works just fine, but when I try to print from a client running my ubuntu 6.04 64bit instead of my prints I get a sheet with the two lines:

-12345X@PJL ENTER LANGUAGE=PCL3
17H10M12AoM1-2Hu300D10L148D14E16Dp0Xg26WXX,,,,,,r1Ab2mP0Yb39VY

I really don't know... what can possibly be?

This is my /etc/cups/printers.conf on the client...

<Printer DeskJet-950C>
Info
Location
DeviceURI ipp://192.168.0.1/printers/DeskJet-950C
State Idle
StateTime 1156334471
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>


Thank you for your help!

---

