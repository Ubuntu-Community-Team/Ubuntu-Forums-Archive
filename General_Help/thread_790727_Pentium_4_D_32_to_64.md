---
title: "Pentium 4 D 32 to 64"
date: 2008-05-11
forum: General Help
---

### Post by Norst on 2008-05-11
I have a Pentium 4 D and I'm running Hardy 32bit. Is there a way to simply switch kernels to the 64bit version? Also is there enough of an advantage to going to 64 to bother? 

I'm pretty sure I can use 64 on my box due to the lshw output: (scroll right in code window)
```
*-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe **x86-64** constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr cpufreq

```

Thx fer any help,
Norst

---

### Post by mannheim on 2008-05-11
You can't switch kernels to the 64 bit version without also switching all the installed libraries and applications to 64 bit also. As far as I have found, this basically means installing from scratch on a new partition.

The pros and cons of 64 versus 32 bit have been discussed in quite a few other threads.

---

### Post by tamoneya on 2008-05-11
switching is much more difficult than just reinstalling.  You first have to recompile the entire kernel which is not a simple task.  Then you need to reinstall every package with the 64 bit version. which will take forever.  You are definately better of with a complete reinstall.  The again, do you really need 64 bit.  Is it really worth the trouble?

---

