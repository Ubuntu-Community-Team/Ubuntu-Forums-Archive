---
title: "Ubuntu 12.04 32bit or 64bit for my system"
date: 2014-03-21
forum: General Help
---

### Post by Joe_Johnston on 2014-03-21
Hello All,

I have a Toshiba Satellite A105-S4014 with 4gigs RAM and upgraded the processor to a 64bit processor and wanted to know if I should be using the 32 or 64bit version of Ubuntu. I noticed my RAM usage in System Monitor this morning after things felt sluggish was 2.2gigs out of 2.9gigs. I rebooted and then checked and it was 320mb RAM without anything open. I am wondering if the 32bit would work better with my system or if you all had any input or tips. Thank you.

---

### Post by grahammechanical on 2014-03-21
32 bit operating systems are not designed to make full use of the capabilities of 64 bit CPUs. A 32bit OS can run on a 64 bit CPU because the architecture of the 64 bit CPU is designed to be backwards compatible with 32 bit operating system and 32 bit programs.

Logic would say that an OS designed for a 64 bit CPU would make better use of that CPU than a 32 bit OS. The day will come when development on 32 bit OSes will cease. Already all new machines have 64 bit CPUs.

Regards

---

### Post by Joe_Johnston on 2014-03-21
Well, that was my thought as well, even though my system was originally only designed for 32bit but now has 64bit processor due to the upgrade.

---

### Post by kurja on 2014-03-21
2.2 out of 2.9 gigs? As in, your OS doesn't see your entire 4 gig ram? Which OS version do you have installed, 32 or 64 bit?

---

### Post by Joe_Johnston on 2014-03-21
I have the 64 bit 12.04 Ubuntu installed but my system was designed for 32bit and apparently it is the motherboard info that the system detects and only allows 3gigs available to the OS. That is why I wondered if 32bit would be better for my situation even though I put a 64bit processor in it.

---

### Post by kurja on 2014-03-21
AFAIK 64bit OS should not run _at all_ on 32bit hardware. Is [this]("http://www.cnet.com/laptops/toshiba-satellite-a105-s4014/4507-3121_7-31812936.html") is your computer? T2400 seems to be core duo which is 32bit, you said you changed the cpu so which kind of cpu do you have?!? What does bios post say about your ram, maybe all of it is not getting recognized?? Did you go to bios setup and save after installing more ram (some older comps require that you do this after ram upgrade)?

---

### Post by kurja on 2014-03-21
can you open terminal and post what is returned with: ```
uname -a
``` and ```
sudo dmidecode --type 17
```

---

### Post by Joe_Johnston on 2014-03-21
Below are the outputs and rebooted right now to check BIOS. The CPU I put in was from a Mac Mini and it was a Core 2 Duo" 1.83 features a 1.83 GHz Intel "Core 2 Duo" (T5600) processor.

> **kurja said:**
> can you open terminal and post what is returned with: ```
uname -a
``` 

Linux joe-Satellite-A105 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

and ```
sudo dmidecode --type 17
```

# dmidecode 2.11
SMBIOS 2.4 present.


Handle 0x0014, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: No Error
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified


Handle 0x0015, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: No Error
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M2
	Bank Locator: Bank 1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

---

### Post by Joe_Johnston on 2014-03-21
I rebooted and went into BIOS and saw 4096megs RAM and saved upon exit.

---

### Post by kurja on 2014-03-21
uh oh. I'm kinda guessing blind here at this point, I would double check that there are no "shared video ram" or alike things in bios, does your machine have a discrete gpu with it's own ram, do you know the motherboard model? You can find that one out with ```
sudo dmidecode | more
``` (look for "base board information" but really I'm not sure where to look next. I would try to find information, maybe a user manual, for the mobo, see if there's anything helpful in there.

---

### Post by kurja on 2014-03-21
I would guess it's a hardware / bios configuration issue anyway, I have a _32_bit & pae 12.04 but I'm seeing all 4 gigs that I have installed and they show as _64_b bit with dmidecode... Best of luck!

---

### Post by slooksterpsv on 2014-03-21
Run the following and post the results:
```

free -h

```
Also:
```

sudo dmidecode --type bios

```

---

### Post by Joe_Johnston on 2014-03-21
> **kurja said:**
> uh oh. I'm kinda guessing blind here at this point, I would double check that there are no "shared video ram" or alike things in bios, does your machine have a discrete gpu with it's own ram, do you know the motherboard model? You can find that one out with ```
sudo dmidecode | more
``` (look for "base board information" but really I'm not sure where to look next. I would try to find information, maybe a user manual, for the mobo, see if there's anything helpful in there.

Below is the output:

```
Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies LTD
    Version: 6.00   
    Release Date: 07/12/2007
    Address: 0xE4480
    Runtime Size: 113536 bytes
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        ACPI is supported
        USB legacy is supported
        AGP is supported
        BIOS boot specification is supported
        Targeted content distribution is supported


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: TOSHIBA
    Product Name: Satellite A105
    Version: PSAA8U-02200U
    Serial Number: 36167216Q                       
    UUID: 9A9ED760-B516-11DA-A70E-00A0D1370AFA
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family: Not Specified


Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Intel Corporation
    Product Name: CAPELL VALLEY(NAPA) CRB
    Version: Not Applicable
    Serial Number: Not Applicable


Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: No Enclosure
    Type: Other
    Lock: Not Present
    Version: N/A
    Serial Number: None
    Asset Tag: No Asset Tag                    
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00001234


Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: U2E1
    Type: Central Processor
    Family: Other
    Manufacturer: Intel
    ID: F2 06 00 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 15, Stepping 2
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
    Version: Intel(R) Core(TM)2 CPU         T5
    Voltage: 3.3 V
    External Clock: Unknown
    Max Speed: 2048 MHz
    Current Speed: 1800 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
```

---

### Post by Joe_Johnston on 2014-03-21
> **slooksterpsv said:**
> Run the following and post the results:
```

free -h

```

There was not an H option so I did L:

free -l
             total       used       free     shared    buffers     cached
Mem:       3071656    2105572     966084          0      68064    1043180
Low:       3071656    2105572     966084
High:            0          0          0
-/+ buffers/cache:     994328    2077328
Swap:      3133436          0    3133436



Also:
```

sudo dmidecode --type bios

```

# dmidecode 2.11
SMBIOS 2.4 present.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: 6.00   
	Release Date: 07/12/2007
	Address: 0xE4480
	Runtime Size: 113536 bytes
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

---

### Post by Joe_Johnston on 2014-03-21
> **kurja said:**
> uh oh. I'm kinda guessing blind here at this point, I would double check that there are no "shared video ram" or alike things in bios, does your machine have a discrete gpu with it's own ram, do you know the motherboard model? You can find that one out with ```
sudo dmidecode | more
``` (look for "base board information" but really I'm not sure where to look next. I would try to find information, maybe a user manual, for the mobo, see if there's anything helpful in there.

Also, it is an on-board video with shared memory as it is an older laptop:

[http://support.toshiba.com/support/modelHome?freeText=1311509](http://support.toshiba.com/support/modelHome?freeText=1311509)

---

### Post by slooksterpsv on 2014-03-21
grep --color=always -i PAE /proc/cpuinfo

Try running that let us know the results.

Ubuntu already has PAE enabled by default, even though the info above flags PAE, that may not always be the case. I want to see if cpuinfo shows that PAE in red. If it does, we'll try more steps, if not, its not a PAE CPU which means 3GB max.

PAE - Physical Address Extension - enables OSes to use more than 4GB of RAM on a 32-bit operating system (in short).

---

### Post by mörgæs on 2014-03-21
No need for the test. It is definitely a PAE processor if you see PAE in the [output]("http://ubuntuforums.org/showthread.php?t=2212474&page=2&p=12964110&viewfull=1#post12964110").

Don't get confused by the forcepae / fakepae deal, which is a different topic.

---

### Post by Joe_Johnston on 2014-03-21
It definitely showed PAE is Red:

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow

---

### Post by Joe_Johnston on 2014-03-21
One more thought, if we discover that everything about my laptop is 32bit besides the processor, then is it advantageous or necessary to use a 64bit OS or just stick with 32bit?

---

### Post by kurja on 2014-03-22
> **Joe_Johnston said:**
> One more thought, if we discover that everything about my laptop is 32bit besides the processor, then is it advantageous or necessary to use a 64bit OS or just stick with 32bit?

Well that's the thing, I'm no guru on the topic but my understanding is that if you already have a 64b cpu and os working together there really shouldn't be anything else not 64bit compliant - still your memory is shown to be "32 bit". Unfortunately we didn't discover your mobo model with those commands. If the gpu is reserving 1 gig for itself, there may be a setting for that in bios (and probably is). There doesn't seem to be any bios updates offered for your machine either. So I don't really know at this point :(

---

### Post by kurja on 2014-03-22
> **Joe_Johnston said:**
> One more thought, if we discover that everything about my laptop is 32bit besides the processor, then is it advantageous or necessary to use a 64bit OS or just stick with 32bit?

You now have the 64b version installed, if it works, there's no advantage from a 32bit os. Also, 64bit hardware is compatible with 32b software.

---

### Post by slooksterpsv on 2014-03-22
REMOVED

Yeah the PAE kernel in Repos is for 32-bit, DO NOT INSTALL IT!

The other option (which I recommend trying) is download Ubuntu 32-bit ISO and boot from it.

---

### Post by kurja on 2014-03-22
isn't pae kernel always 32bit

---

### Post by slooksterpsv on 2014-03-22
That's what I was unsure of, it should only be 32-bit, but.... I don't know...

---

### Post by kurja on 2014-03-22
Trying to install a 32bit kernel on 64bit install sounds like asking for trouble. And I already have a nosebleed (flu, blowing my nose too much), please don't advice anyone to change to a kernel you don't know will work with their install.

---

### Post by slooksterpsv on 2014-03-22
Uh... I said to see if there was a PAE kernel in repos. It should be a 64-bit kernel. The 32-bit idea was to get the 32-bit ISO and boot from it.

Yeah the PAE kernel in a 64-bit distro will try to put 32-bit on the system. I removed that post and just recommended to download Ubuntu 32-bit and boot from it and see what the memory says.

---

### Post by mörgæs on 2014-03-22
Again, please let all talk about PAE rest. It only adds confusion.

Virtually all processors younger than 20 years have PAE, though a few of them (a corner case of some old Pentium M's) do not display it right away. 
Ubuntu 12.04 32 bit is PAE enabled from birth.
End of story.

---

### Post by Joe_Johnston on 2014-03-22
I really appreciate all the input. I guess the thing that has had me wondering is the fact that this laptop originally came with the following:

Processor / Chipset
CPU Intel Core Duo T2400 / 1.83 GHz
Number of Cores Dual-Core
Cache L2 cache - 2 MB
Front Side Bus 667 MHz
Chipset Mobile Intel 945GM Express
Platform Technology Intel Centrino Duo
Features Execute Disable Bit capability,
Enhanced SpeedStep technology,
Power-optimized processor system bus
Memory
RAM 1 GB
Max RAM Supported 4 GB
Technology DDR2 SDRAM
Speed 533 MHz / PC2-4200
Slots Qty 2

The only two things I changed was the CPU to the Intel® Core&#8482;2 Duo Processor T5600 (2M Cache, 1.83 GHz, 667 MHz FSB) and update the system to 4gigs RAM from 1gig. So I am wondering if the rest of my laptop is 32bit but the CPU is the only 64bit capable piece and that I may be better off with the 32bit Ubuntu than the 64bit. What do you all think? Is it giving me any benefit to have the 64bit Ubuntu just for the CPU?

---

### Post by Joe_Johnston on 2014-03-22
One more quick update: I happened to have a USB 12.04 32bit thatI use for installing on customers systems and decided to boot from it and look around. The system monitor still onlys sees 3gigs of RAM available so apparently this laptop holds the other gig for something and is not available to the system. I looked around the BIOS settings and there is nothing of note to change that would enable more memory. 

Now, I am not sure what to do. Should I just use the 32bit version since the only 64bit hardware I have is the CPU or do I use the 64bit version since at least one thing can utilize it?

---

### Post by oldos2er on 2014-03-22
If your processor is 64-bit, why consider 32-bit at all? At least this is the way I look at it. Also I don't understand what other hardware has to do with it; hard disks and RAM don't care about the bitness of the data they encounter.

---

### Post by Joe_Johnston on 2014-03-22
> **oldos2er said:**
> If your processor is 64-bit, why consider 32-bit at all? At least this is the way I look at it. Also I don't understand what other hardware has to do with it; hard disks and RAM don't care about the bitness of the data they encounter.

I appreciate this input and agree with you. Thank you all for the input and I am sticking with 64bit as it seems to run quite well and I am worrying over nothing!

---

### Post by kurja on 2014-03-23
> **Joe_Johnston said:**
> I appreciate this input and agree with you. Thank you all for the input and I am sticking with 64bit as it seems to run quite well and I am worrying over nothing!


That's right, unless you specifically need more available ram to get your work done this is really a non-issue. "If it works, don't fix it", right? 


Itching to find out what is the cause of this however, I went through your machine's [specs]("http://www.cnet.com/laptops/toshiba-satellite-a105-s4014/4507-3121_7-31812936.html") again and looked a little harder at the chipset; Your machine indeed does allocate ram to video use but should not take a whole gig in any case, _*but*_ I found users on various forums talking about this and an official [Lenovo page ]("http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-62487")saying that, I quote, " Intel Chipsets 945GM and 945PM do not support more than 3GB system memory (RAM), even when a 64-bit operating system is installed"


I guess that's it then :-/

edit - If Toshiba promised you upgrade-ability up to 4GB maybe it would be best to just contact their support, see what they have to say about this.

---

### Post by Joe_Johnston on 2014-03-25
> **kurja said:**
> That's right, unless you specifically need more available ram to get your work done this is really a non-issue. "If it works, don't fix it", right? 


Itching to find out what is the cause of this however, I went through your machine's [specs]("http://www.cnet.com/laptops/toshiba-satellite-a105-s4014/4507-3121_7-31812936.html") again and looked a little harder at the chipset; Your machine indeed does allocate ram to video use but should not take a whole gig in any case, _*but*_ I found users on various forums talking about this and an official [Lenovo page ]("http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-62487")saying that, I quote, " Intel Chipsets 945GM and 945PM do not support more than 3GB system memory (RAM), even when a 64-bit operating system is installed"


I guess that's it then :-/

edit - If Toshiba promised you upgrade-ability up to 4GB maybe it would be best to just contact their support, see what they have to say about this.

Thank you for this info and it does clear things up.

---

