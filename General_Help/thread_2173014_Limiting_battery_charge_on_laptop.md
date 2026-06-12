---
title: "Limiting battery charge on laptop"
date: 2013-09-07
forum: General Help
---

### Post by SMOKE5 on 2013-09-07
Hello, Im running Ubuntu 13.04 on my Compaq Presario CQ57
I wanted to limit my max battery charge to 80% But Im unable to find any help.
I was looking at this tutorial, but Im not sure if it will work on my PC
[http://ubuntuforums.org/showthread.php?t=2148044](http://ubuntuforums.org/showthread.php?t=2148044)
Thanks for any help

---

### Post by oldrocker99 on 2013-09-07
Looking at that laptop's specs, I see no reason why that page's instructions wouldn't work. It's certainly worth a try.

---

### Post by tgalati4 on 2013-09-07
That module in the link will only work for Thinkpads.  You would need to find a module for that model of machine.  An alternative is to use a torque timer--one of those rotary timers that have on and off periods.  Just have it cycle off for a few hours late at night.  That way you get a charge early in the evening, the battery is off say from midnight to 5 am, then charged just before the next day's use.

tgalati4@tpad-Gloria7 ~ $ modinfo tp_smapi
filename:       /lib/modules/2.6.28-19-generic/kernel/ubuntu/misc/tp_smapi.ko
license:        GPL
version:        0.37
description:    ThinkPad SMAPI Support
author:         Shem Multinymous
srcversion:     7774CFE98BA09B3E60EA564
depends:        thinkpad_ec
vermagic:       2.6.28-19-generic SMP mod_unload modversions 586 
parm:           debug:Debug level (0=off, 1=on) (int)

Another strategy that I use to prolong battery life is to buy 2 or 3 batteries and rotate them every 2 to 3 months, leaving the others at 40 or 50% charge during the storage time.

You can use *acpitool* and a fancy script with *notify-send* to tell you when you are at 80% charge and manually plug and unplug, but that is a pain.  Charge circuits are normally controlled by the laptop's acpi system, so unless you have a module that allows you to control it, you are forced to use a crude method.


tgalati4@tpad-Gloria7 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : 41210 mWh, 96.17%
    Design capacity    : 51830 mWh
    Last full capacity : 42850 mWh, 82.67% of design capacity
    Capacity loss      : 17.33%
    Present rate       : 0 mW
    Charging state     : charged
    Battery type       : rechargeable, LION
    Model number       : IBM-92P1091
    Serial number      :    89

It's funny, I can control the charge on a Thinkpad in linux, but I have to boot into Windows to see the number of charge cycles.

---

### Post by SMOKE5 on 2013-09-07
> **tgalati4 said:**
> You would need to find a module for that model of machine.

How would I go about doing that?
Ive Google'd it but didnt find anything.

---

### Post by tgalati4 on 2013-09-07
Write your own module.  It will take some cooperation of the vendor Compaq, now HP.  Look at the source code for tp_smapi.  Send some emails to HP developers and see what response you get. 

If you are dealing with a weak battery, similar to this post:  [http://forums.mydigitallife.info/threads/5828-Manually-Stop-Battery-from-Charging](http://forums.mydigitallife.info/threads/5828-Manually-Stop-Battery-from-Charging)
then you need to get a new battery, because the charging circuit is designed not to charge batteries that show signs of an internal short.  That could cause a fire, and your data is not worth more than your house, but probably worth more than a new battery pack.

How many cycles are on the battery?  Batteries are only good for 300 cycles or 3 years which ever comes first.

---

### Post by SMOKE5 on 2013-09-08
> **tgalati4 said:**
> How many cycles are on the battery?  Batteries are only good for 300 cycles or 3 years which ever comes first.

Ive had this pc for about a year and a half. I always have the charger plugged in.
Will this hurt the battery having it connected all the time?
Thanks for the help BTW

EDIT:
Also, with a Bios mod can I control the battery max charge ?

---

### Post by tgalati4 on 2013-09-08
Yes, generally, a battery plugged in all the time will have a shorter life.  But modern machines (anything in the last 5 years) have pretty sophisticated charging circuits.  Chargers will go to trickle charge when the battery is full.  Some shut off until the battery drops to 95% or 90% and then charge back up to 100%.  Many have a safety circuit that won't charge a battery that shows signs of a weak cell.  All it takes is one cell of a 6-cell battery pack to go bad and you have lost the battery.

So, if you add an external timer that shuts off the charger at night, presumably you could slightly increase the battery life.  But again, the chemistry of lithium-ion batteries is such that they will corrode and short out after 3-5 years whether used or not.  If you use the battery every day on a bus, then you will blow through 300 cycles in a year and a half.  

A quick web search shows that Presario batteries are prone to failure at 18 months.  So perhaps Compaq/HP used lower-quality batteries in these machines.

If you can figure out how to modify the BIOS/ACPI, then perhaps you can change the charging cycle, but you would get better results finding a higher-quality replacement battery.

---

### Post by SMOKE5 on 2013-09-09
Ok then, thanks man

---

