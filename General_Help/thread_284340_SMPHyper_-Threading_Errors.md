---
title: "SMP/Hyper -Threading Errors"
date: 2006-10-25
forum: General Help
---

### Post by Old Pink on 2006-10-25
Hi there. 

I'm using a 2.66Ghz Pentium 4 Processor, and dmesg gives the following:> [17179569.184000] SMP mptable: bad signature [0x0]!
[17179569.184000] BIOS bug, MP table errors detected!...
[17179569.184000] ... disabling SMP support. (tell your hw vendor)> [17179572.216000] CPU: Hyper-Threading is disabledNow, I got these errors on the 386 kernel, and after some searching realised I was eligible for the 686 kernel. So, I installed linux-686, linux-686-smp and linux-generic using aptitude.

Only linux-generic was added to the grub list, and I still have these errors. I checked /boot, and vmlinuz-2.6.17-10-generic was the only kernel added using the above updates. So, I guess linux-686 and linux-smp are all included within linux-generic? :-k

I've checked BIOS for anything SMP/Hyper-threading related, but there's actually very few settings in there, none of which are related to my problem. :( 

Oh, and "ht=on" or "HT=on" at boot don't *actually *turn ht on, as I've been told they would. :( 

Attached are:[LIST]
[*]A screenshot of /boot contents
[*]dmesg in full (a txt file inside an archive, it was bigger than 19.5kb)
[*]My menu.lst file (as a txt file)[/LIST]

---

### Post by Old Pink on 2006-10-25
Nobody's even looked at the files? :(

---

### Post by Old Pink on 2006-10-25
Right, thanks to everyone who helped! [-(

---

### Post by MattJ100 on 2006-10-25
Now I'd help if I knew tha answer ^^

Maybe pay heed to what it says, and flash your BIOS? How new is your motherboard? Mine has an option for HT on/off. I'm using a 3.2GHz P4 (64-bit)

EDIT:

```
matthew@matthew-desktop:~$ dmesg | grep SMP
[17179569.184000] Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179571.260000] SMP alternatives: switching to UP code
[17179571.752000] SMP alternatives: switching to SMP code
[17179633.788000] apm: disabled - APM is not SMP safe.

```

---

