---
title: "Lenovo G50-45 laptop freezes with green lines, restarts itself, refuses base updates"
date: 2016-08-12
forum: General Help
---

### Post by giga+bytes on 2016-08-12
I bought this laptop 2 or 3 months ago for our first Ubuntu-only computer. Model 80E3, S/N PFOESNH5. Before putting in the battery or starting it for the first time, I swapped the factory HDD with the OEM Windows 10 pre-install for a new Samsung 850 EVO SSD. I also removed the factory 4GB 1600 RAM and put a stick of 8GB 1866. Then I installed Ubuntu 14.04 from a USB flash drive, letting Ubuntu auto-configure the partitions (BIOS is set to UEFI mode). I have been having constant system lockups/freezing with green lines across the screen, for no reason the computer restarts itself, and it doesn't like to install Ubuntu base updates. I discovered that I hadn't disabled secure boot in the BIOS, so did that and re-installed Ubuntu, but it hasn't helped. I just double-checked the BIOS version and found it has A2CN4OWW, while the Lenovo support page for this model says the newest BIOS version is A2CN_38_OWW. I also checked the RAM for errors with 6 hours of memtest, and found none.

A few days ago I built a new mini Ubuntu PC (also Ubuntu-only, no other OS), and have not had a single problem with it, so I know I didn't make any mistakes with the installation. The only thing I did differently was manually configure the partitions, following advice from experts in these forums.

I could sure use some help! Has anyone with the same, or a similar laptop had problems like this?

---

### Post by giga+bytes on 2016-08-13
Did I post this thread in the wrong forum?

---

### Post by banceu_sergiu_ione on 2016-08-14
Hello giga

For the updates, what is the error output of :

```
 sudo apt update 
```
```
 sudo apt upgrade 
```

Does your pc restart itself when it get overheat ?
Does it lock/freez when the monitor turn off? Do you have the screen off option active/inactive and Lock option on/off?
Did you installed the graphic proprietary drivers?

---

### Post by giga+bytes on 2016-08-15
I finally got some time to check on this. For about a week we have been using those sudo commands instead of the software updater, and it seems to now be installing the base updates. I'm not sure why the software updater wouldn't install those updates.

The laptop never overheats. It runs very cool, and we don't do anything intensive that stresses it in any way. It just randomly restarts without warning or cause, sometimes while offline and sometimes while online.

The screen is set to turn off, but not to lock. The laptop has never frozen/locked-up while the screen is off, only while something is being displayed.

We have only the open-source drivers that Ubuntu installed itself automatically.

---

### Post by QIII on 2016-08-15
Hello!

It might be worth ruling out hardware faults by popping the Windows disk back in and running that for a bit.

---

