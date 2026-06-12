---
title: "Ubuntu 18.04 sees half the RAM on three systems"
date: 2019-03-01
forum: General Help
---

### Post by Lambertus on 2019-03-01
ISSUE: 3 systems see half of the installed RAM

Installed Ubuntu 18.04 on three desktop computers within the last year. Two are AMD A8 and the other an Intel dual core 6600.
Each install shows only half the available RAM.
The latest install was on the Intel system and it was running Ubuntu 14.04 and showed the existing 6GB RAM. Now only 3GB.

Checked the RAM on each system. Each chip set is good.
Moved the RAM sets from one slot to another. No matter what combination of slots and chip sets are chosen, the available RAM is always half that plugged in.

What am I doing wrong?
or what is peculiar about 18.04 that makes this happen?

---

### Post by Autodave on 2019-03-01
I have 8 systems here and just checked them: all are showing the correct amount.  What program are you using to report the amount of RAM?

---

### Post by ajgreeny on 2019-03-01
Just to check; are you using a 64bit OS or a 32bit?

Let's see the output of ```
uname -a
``` in terminal.

---

### Post by Lambertus on 2019-06-06
64 bit
uname for one set up is = Linux lambertus 4.15.0-51-generic #55-Ubuntu SMP Wed May 15 14:27:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
RE: RAM report. BIOS shows the RAM as half, system monitor shows half, setting About shows half.
If one RAM card is used. the system reports half its memory.


[TABLE]
[TR]
[TD="align: center"][/TD]
[/TR]
[/TABLE]

---

### Post by ajgreeny on 2019-06-06
What output does the command ***free -mw*** give you?

---

### Post by Lambertus on 2019-06-06
free -mw
              total        used        free      shared     buffers       cache   available
Mem:          15940        2583       10738          69         263        2354       12957
Swap:          2047           0        2047

System has 32GB RAM installed (4x8).

---

### Post by oldfred on 2019-06-06
If BIOS shows RAM at half, then your system does not support that much RAM.
If older system, like the Intel dual core, then motherboard may not support that much RAM.
Does motherboard say it supports that much?

---

### Post by Lambertus on 2019-06-06
motherboard is: M5A99X EVO R2.0
and supports 32GB with 64 bit OS.

though that is a red herring, because if I leave one 8GB chip in the RAM slots, the system shows 4GB RAM: always half.

---

### Post by oldfred on 2019-06-06
Are all 4 memory cards the same? Same brand, spec, speeds etc.?

Do you have latest UEFI/BIOS for that motherboard?

---

### Post by Lambertus on 2019-06-06
The memory is the same brand, and specifications on all three of the computers that have this issue.
The bios on this particular computer (m5a99x evo r2.0 and amd fx8350) is the latest (v. 2501).

Thank you for sharing your tips on what to check.

On my wife's computer Ubuntu 14.04 recognized all 6 GB of installed RAM. When Ubuntu 18.04 was installed on the computer, it would only recognize 3 GB. The installation of 18.04 was the only change made to the computer. On mine, I bought the motherboard with CPU and Memory (the M5A99x) and installed 18.04 and it only recognized half the memory so I figured it was a flaw in the motherboard slots or the chips, until I checked each one separately.

---

### Post by oldfred on 2019-06-06
Still if BIOS does not see the RAM, the operating system will not see it.
BIOS writes hardware info to hard drive for operating system to know what it has to work with. So unless BIOS correctly sees full RAM, you will not get more RAM in Ubuntu.

---

### Post by QIII on 2019-06-06
If BIOS shows the RAM at 1/2 of installed, I think you might get more timely advice on an ASUS forum.

Ya never know, though.  Just the right person may post right after me.

---

