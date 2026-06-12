---
title: "Overheating: ACPI/Fan Control (Edgy)"
date: 2007-01-18
forum: General Help
---

### Post by sadams on 2007-01-18
Hi All,

I have a problem regarding overheating/acpi control of the CPU fan.
Essentially: when the temp gets hot it seems the CPU fan cannot be activated, resulting in the temp warning siren going off and the temp rising and rising as reported in /proc files.

This (or something like it) has been reported elsewhere but I believe not properly addressed/fixed - correct me if I am wrong :-)

Below is a full report - I hope it helps.

1) Intro:
=========
I have witnessed this a few times and have a reproducible case.
I have done some initial research (googling/forum searching) and this has been reported/discussed - however it seems people have treated it as a problem with the message, rather than a an actual problem with the acpi/fan control. 

I think this is potentially a dangerous problem as it could cause  overheating (and consequent hardware damage?)

Some system info:
-----------------
Running Edgy
uname -a
Linux shaft 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

from: cpuinfo
------
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3007.288
cache size      : 512 KB
-------

from: /proc/acpi/thermal_zone/THRM
----------------------
% more *
::::::::::::::
cooling_mode
::::::::::::::
cooling mode:   active
::::::::::::::
polling_frequency
::::::::::::::
<polling disabled>
::::::::::::::
state
::::::::::::::
state:                   ok
::::::::::::::
temperature
::::::::::::::
temperature:             49 C
::::::::::::::
trip_points
::::::::::::::
critical (S5):           100 C
active[0]:               85 C: devices=0xdffe3bd0 
---------

2) Problem description
======================
When I run something CPU intensive (i.e. wav => mp3 encoding with lame) for a period of time (a few minutes plus) I get the following symptoms:
 a) CPU load at 50% (is 100% of a virtual CPU) as expected for Hyper Threading P4
 b) Temp reported in /proc/acpi/thermal_zone/THRM/temperature climbs/increments steadily as job continues
 c) when temp reaches 85C (the threshold in trip_points file)  warnings are generated in /var/log/messages:
------------
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Unable to turn cooling device [dffe3bd0] 'on'
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Unable to turn cooling device [dffe3bd0] 'on'
------------

 d) A minute or two later there is an "alarm sound" from the PC speaker (i.e. NOT the audio system) - a scary "siren like sound".... my machine is in pain... it is calling to me.... it needs help !!!
 e) If I ^Z (suspend) the job in the shell.... obviously the CPU usage drops to nothing... and I watch the reported temp decline back to a steady state.
 f) if I resume the job (fg in shell) the process is repeated (temp climbs - log file messages - alarm sounds)


3) Conclusions:
===============
I believe that the message reported is a genuine one... in that the system detects the temp threshold correctly, and attempts to start the fan. For some reason (I have no idea why) this fails.... and is reported accordingly in the log file. If I do not intervene (i.e. suspend job) the temp climbs and climbs.. my machine screams in pain (er.. issues audible alert).
Would this go on until a melt down ?
Is it dangerous ?

It certainly seems straightforward to me.
It certainly has only occurred since I move to Edgy (previously ran Warty and Hoary on same machine - never had this).


4) FIX IT!   :-)
==========
Can someone give an authoritative reply to this - or tell me how (else) I should report it ?

Many thanks - Steve

---

### Post by sadams on 2007-01-19
hello again - no responses to this... am I in the wrong forum - should it go to "Hardware & Laptops" maybe?

Is it possible to "cross-post" or should I create a duplicate in the "Hardware & Laptops" forum ?
Or maybe to somewhere else - what's this Launchpad thing i see mentioned?

I would appreciate a steer from somebody with more experience of the forums here :-)
Please forgive any foolishness :-)
Regards,
  Steve.

---

