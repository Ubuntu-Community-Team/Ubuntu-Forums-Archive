---
title: "Google Chrome will not start - Illegal Instruction"
date: 2015-12-10
forum: General Help
---

### Post by Azdour on 2015-12-10
Hi,

It's been sometime since I have had problems with our Xubuntu set up here but after updating our Xubuntu server to:

```
Linux Office-Server 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:34:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Google Chrome refuses to start. If I run it from the terminal I get:

```
Illegal instruction (core dumped)
```

I am starting to think it is kernel related although I have found nothing via Google that matches my issue.

Things I have tried:

[LIST]
[*]Running without extensions
[*]Removing the google-chrome directory from .config
[*]Running as a different user
[*]Creating a brand new account
[*]Reinstalling Chrome in case of a corrupt file
[/LIST]

None of the above got it to work.

We run a DRBL system here and the clients use the same google-chrome-stable executable direct from the server and they all work.

The only difference is that they are running on:

```
Linux client1 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

That is what has got me thinking it is kernel related and the server has no other kernels - may be I was too eager to remove unused ones because of limited space.

I also searched on this forum and found an October 2015 post about Google no longer supporting older pentium 4 processors that do not support SSE2.  But our server has this (highlighted in bold below):

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Xeon(TM) CPU 3.00GHz
stepping	: 3
microcode	: 0x5
cpu MHz		: 2992.759
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
**flags**		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse **sse2** ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr
bogomips	: 5985.51
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

Is there anything else I can do or test before submitting it as an issue?

---

### Post by tgalati4 on 2015-12-10
Try running the older kernel--which you deleted.

If it works, then file a bug against the newer kernel.

---

### Post by Azdour on 2015-12-10
Hi,

Thanks.

Have now tried that and I still cannot get it to work...  May be a hardware issue?  Runs on clients using the same executable but not on the server.

---

### Post by llamabr on 2015-12-10
It's almost certainly a kernel issue.  please post:


    your /etc/portage/make.conf
    the output of emerge --info
    one of the stanzas of /proc/cpuinfo (you will see it is repeated per core, we only need the info once)

---

### Post by efflandt on 2015-12-10
It is not a general issue between that kernel and Chrome with regular Ubuntu, but maybe something specific to your system. Chrome works fine on a 5 yr old i5 650 3.2 GHz w/GTX 750 Ti (nvidia-358).```
efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:34:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

efflandt@XPS-8100-1404:~$ dpkg-query -l google*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
ii  google-chrome-stable        47.0.2526.80-1     amd64              The web browser from Google

efflandt@XPS-8100-1404:~$ google-chrome-stable
efflandt@XPS-8100-1404:~$
```Return prompt was after exiting Chrome

---

### Post by sandyd on 2015-12-10
Hang tight, the fix may be coming:
[https://code.google.com/p/chromium/issues/detail?id=525751](https://code.google.com/p/chromium/issues/detail?id=525751)

[https://code.google.com/p/chromium/issues/detail?id=544160#c20](https://code.google.com/p/chromium/issues/detail?id=544160#c20)
You're on a netburst cpu from the same era as the processors that were affected, probably same issue

dmidecode can probably provide some more info about the processor and determine exactly what model it is

Ex:
```

~# sudo dmidecode -t processor
# dmidecode 2.12
SMBIOS 2.4 present.

Handle 0x0401, DMI type 4, 32 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Other
	Manufacturer: Bochs
	ID: F2 06 03 00 FF FB 8B 0F
	Version: Not Specified
	Voltage: Unknown
	External Clock: Unknown
	Max Speed: 2000 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: Not Provided
	L2 Cache Handle: Not Provided
	L3 Cache Handle: Not Provided
```

---

### Post by Azdour on 2015-12-11
Hi,

I think you maybe right sandyd - works on clients but not on server so it's probably the age of CPU on the server.

Here is the dmicode you requested:

```
# dmidecode 2.12
SMBIOS 2.3 present.

Handle 0x0400, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
	ID: 43 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 3
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Not Specified
	Voltage: 1.5 V
	External Clock: 800 MHz
	Max Speed: 3800 MHz
	Current Speed: 3000 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: Not Provided

Handle 0x0401, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
	ID: 00 00 00 00 00 00 00 00
	Signature: Type 0, Family 0, Model 0, Stepping 0
	Flags: None
	Version: Not Specified
	Voltage: 1.5 V
	External Clock: 100 MHz
	Max Speed: 3800 MHz
	Current Speed: Unknown
	Status: Unpopulated
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0702
	L2 Cache Handle: 0x0703
	L3 Cache Handle: Not Provided

```

---

