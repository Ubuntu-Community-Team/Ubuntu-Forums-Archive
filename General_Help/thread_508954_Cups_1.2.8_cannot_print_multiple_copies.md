---
title: "Cups 1.2.8 cannot print multiple copies"
date: 2007-07-24
forum: General Help
---

### Post by tux43 on 2007-07-24
Hi All,

I have an Ubuntu 7.04 server running CUP 1.2.8 and I am having problems with printing when multiple copies are selected. I have looked through various forums and I cannot find a solution but can see a few posts with a similar problems.

I am running two HP printers a 1300 and a 1320n, below is the printers.conf file. If I do the following only one copy is printed rather than 5 which is not correct because -n should be the number of copies.

cat filename | lp -n 5 -d printer_name


Has anybody solved this?

Thanks

------------------------------------



# Printer configuration file for CUPS v1.2.8
# Written by cupsd on 2007-07-14 20:57
<Printer emu>
Info EMU hp LaserJet 1300n
Location Local Printer
DeviceURI socket://emu
State Idle
StateTime 1184412406
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer snapper>
Info SNAPPER hp LaserJet 1320 series
Location Local Printer
DeviceURI socket://snapper
State Idle
StateTime 1184412413
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by NewJack on 2007-07-25
Just a quick question for you.  Why are you using CUPS instead of the HPLIP drivers?  I believe those printers are supported by HPLIP.  Give it a shot.

---

### Post by tux43 on 2007-07-25
OK - Tried using HPLIP and pointed CUPS to it as per the documentation on the HPLIP web site. I still get the same problem.

---

### Post by NewJack on 2007-07-26
Ok,  try this....

- Go to Administration>Printing and remove your printers\

- Now add one printer and when you get to the part about which driver you want make sure to use HPLIP.

- Repeat for the second printer.

When I first installed my 1200 LJ printer, I had the default driver installed before finding out about HPLIP so I just tried changing it and nothing worked.  When I did a clean "Add" of the printer pointing it to use the HPLIP from the start, it worked without a hitch.

---

