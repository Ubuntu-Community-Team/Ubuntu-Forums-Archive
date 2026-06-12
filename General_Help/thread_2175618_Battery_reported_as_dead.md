---
title: "Battery reported as dead"
date: 2013-09-20
forum: General Help
---

### Post by benjamindaines2 on 2013-09-20
This is something that I've noticed as a problem with Linux for a while.  There doesn't seem to be any pattern to when it happens, but every now and then my battery meter will suddenly say that my battery is dead.  Since I'm saying this is a problem, my battery obviously isn't dead.  If I put the system to sleep and wake it back up my battery will be reported accurately again.  Can anyone help me determine what is causing this issue and perhaps find a solution?  I've been googling this for ages and have yet to find any useful info on it. 

Thanks.

---

### Post by tgalati4 on 2013-09-20
Install *acpitool* and monitor the battery statistics in a terminal window.

tgalati4@Mint14-Extensa ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 100.0%
    Design capacity    : 4000 mA
    Last full capacity : 3825 mA, 95.62% of design capacity
    Capacity loss      : 4.375%
    Present rate       : 0 mA
    Charging state     : Full
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315

Take note of the values coming out of sleep (when the battery appears normal) and then again after the indicator reports "dead".

You can also get statistics graphs by clicking on the icon then click on the battery.  Look at the statistics when working on battery for an hour and see if you get a linear decline in capacity during a work session.  If you get wild swings in the data, then there may be something wrong with the battery contacts or the power circuitry that is causing dropouts in data and hence a "dead" warning.

---

### Post by benjamindaines2 on 2013-09-20
> **tgalati4 said:**
> Install *acpitool* and monitor the battery statistics in a terminal window.

tgalati4@Mint14-Extensa ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 100.0%
    Design capacity    : 4000 mA
    Last full capacity : 3825 mA, 95.62% of design capacity
    Capacity loss      : 4.375%
    Present rate       : 0 mA
    Charging state     : Full
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315

Take note of the values coming out of sleep (when the battery appears normal) and then again after the indicator reports "dead".

You can also get statistics graphs by clicking on the icon then click on the battery.  Look at the statistics when working on battery for an hour and see if you get a linear decline in capacity during a work session.  If you get wild swings in the data, then there may be something wrong with the battery contacts or the power circuitry that is causing dropouts in data and hence a "dead" warning.
Here's the output when the battery is reported as **dead**:
```
ben@ben-MacBookPro:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 46640 mWh, 73.97%, 02:33:50
    Design capacity    : 69000 mWh
    Last full capacity : 63050 mWh, 91.38% of design capacity
    Capacity loss      : 8.623%
    Present rate       : 18191 mW
    Charging state     : Discharging
    Battery type       : Unknown 
    Model number       : bq20z4510NGD



```

---

### Post by tgalati4 on 2013-09-20
You didn't mention that it was a macbook pro.  Macbooks (and Apple computers in general) have some sophisticated (meaning quite proprietary) battery management circuits.  It's possible that the acpi system performs a battery test every so often, and if it fails sends a flag to the acpi system, which then throws an indicator.

Your battery doesn't look that old.  If this is a dual-boot system, boot in OS X and look in the "About this Mac" and look for the number of charge/discharge cycles for this battery.  Otherwise, I would physcially remove and reinstall the battery several times (while the computer is off) and try to get the contacts clean.  Also with a toothpick (non metallic), check for stiffness of the gold battery tabs.  A loose tab could cause erratic power during charge or discharge.

Look through the statistics graphs for jumpy behavior while on battery.

Are you running Ubuntu under a VM under OS X?  If so, then perhaps there is a communication issue with the acpi messaging through the VM.

---

