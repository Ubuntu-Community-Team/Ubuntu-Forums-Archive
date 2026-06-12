---
title: "SMP kernel installed, but won't come up???"
date: 2007-01-29
forum: General Help
---

### Post by geek777 on 2007-01-29
Hey All,

Please forgive me if this is the wrong forum area for this:

I have a new work station here at the office and have never had this problem with earlier machines, but perhaps it is something I have done (or not done) causing this problem.

I have a Dell GX620 which is an Intel Pentium D (same as Core Duo I am told, although i think it's different but still SMP capable).

I am dual booting Vista and it is clearly running 2 CPU's (evidenced from task manager ) so I know the BIOS is correctly configured (dual core enabled = true).

Some history:
========

So, I installed Vista onto sda1 and Ubuntu after the fact onto sda2, install was clean, no error but GRUB seemed hosed so I had to reconfigure grub after ward such that hd0,1 was mapped for Ubuntu and hd0,0 was for Vista.../boot/grub/menu.lst edited and dual-booting was set.

I did an apt-get update, then apt-get install linux-686-smp, no errors displayed, ended with success...reboot...


cat /proc/cpuingo...shows only one CPU:

~~snip~~~

 cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 2992.631
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm
bogomips        : 5990.16

~~~/snip~~~

I then did a grep through dmesg (dmesg | grep -i CPU and found the following:

~~~snip~~~

[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] Initializing CPU#0
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e4bd 00000000 00000001
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e4bd 00000000 00000001
[17179569.268000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e4bd 00000000 00000001
[17179569.268000] CPU: Intel(R) Pentium(R) D CPU 3.00GHz stepping 04
[17179572.928000] ACPI: Getting cpuindex for acpiid 0x2
[17179572.928000] ACPI: Getting cpuindex for acpiid 0x3
[17179572.928000] ACPI: Getting cpuindex for acpiid 0x4
[17179596.352000] acpi_cpufreq: Unknown symbol cpu_online_map

~~~/snip~~~

It "feels" like maybe menu.lst needs correction to point to the proper kernel initrd or img perhaps???


I was under the impression, the dep package would automagically configure the grub menu/lst as needed?

Looking in /boot, i don't see anything looking like a 686 kernel....but if I check that status of the package linux-686-smp it shows installed so i am at a loss.

Any help or suggestions welcomed.

---

### Post by geek777 on 2007-01-29
Nobody has any ideas?

I will gladly provide more detail if you have any ideas...I upgraded my bios and double checked again that dual core support was enabled...still, vista shows 2 cpus and Ubuntu only one when doing a cat of /proc/cpuinfo

---

### Post by Ramses de Norre on 2007-01-29
Which ubuntu version do you have? The smp kernels are deprecated since dapper, in dapper the 686 and k7 kernels have smp enabled by default (so if you've got dapper you need to install **linux-686**), on edgy those two kernels are made into one, the generic kernel (with smp enabled by default, so if you've got edgy you need to install **linux-generic**).
I hope this helps, I don't have a dual core cpu myself so I can't help you any further...

---

### Post by doundounba on 2007-02-24
This happened to me. I'm not sure how or when though, since I'm quite sure that I had both processors working previously. But somehow I wound up with the -386 kernels before the -generic ones in my menu.lst.  (I also had hiddenmenu turned on, with a short timeout of 3 seconds, so it was difficult to see what was happening at boot time.)  This meant I was booting the non-smp enabled kernel by default.  Once I noticed, what I did was simply edit menu.lst to change the order and put the -generic kernels first, and everything's fine now.  (Note that I also had a line that said "default 0", which means by default the machine boots the first kernel in the list.  If yours doesn't say that, your solution won't be the same as mine.)


This is what your menu.lst should look like (assuming you're on Edgy, like me):
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

[... VARIOUS OTHER DEFAULTS AND OPTIONS HERE ...]

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/mapper/Ubuntu-root ro single
initrd          /initrd.img-2.6.17-11-generic


[PROBABLY MORE STUFF AFTER THIS]

```

---

### Post by Surgeon General on 2007-04-21
I upgraded to Edgy, was using linux-686 for SMP, then found out that the stock kernel from the upgrade doesn't support SMP.

Why, in Edgy, we have to use the generic one instead of the 686??

---

### Post by malus_Diaz on 2007-09-29
Thank you! 
 Solved my missing cpu problem! Go boot list selection.

---

