---
title: "Google Chrome partial crash"
date: 2016-02-24
forum: General Help
---

### Post by Azdour on 2016-02-24
Hi all,

I have four computers with Xubuntu 14.04 on. They are all the same make and processor.

When Chrome is used on them, there have been occasions when creating a new tab either creates a new tab that is empty (should default to google.co.uk from the settings) or the new tab shows black blocks.

Either way it renders Chrome not usable.  You can create more new tabs and type in URLs into the address bar but the tabs remain empty or just display black blocks.

I have tried to run Chrome from the terminal to see if anything gets output there but nothing does.

The issue does not always happen, there seems to be a randomness to it but it is getting more frequent.

All the computers are running on the 64bit kernel 3.13.0-77-generic.

The CPU for the machines is:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 9
microcode	: 0x3
cpu MHz		: 3192.112
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 6384.22
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 9
microcode	: 0x3
cpu MHz		: 3192.112
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 6384.22
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

I've googled for 'chrome and black squares' and while there are many reports of the black squares, none of the reported issues say that is stops the rendering of the webpage.

Is there something else I should be doing to track this issue down?

---

