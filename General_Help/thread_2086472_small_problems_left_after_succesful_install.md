---
title: "small problems left after succesful install"
date: 2012-11-21
forum: General Help
---

### Post by jbart0312 on 2012-11-21
Hey.

So, finally (sigh of relief) got my Ubuntu back. Everyone knows how troubling computer systems can be at times. I had to trade my laptop in for a desktop, and it has win xp . Of course I went to the Ubuntu download and tried to get the latest version. That didn't work; due to the hardware on the build I purchased for 60 usd. What did work was Lubuntu, so I am happy. I am having an issue with the OS dropping out and restarting randomly. When it comes back online the mouse cursor is missing. I hope this is a flag to someone and they can illuminate on my problem. So, my new OS is a little unstable. It might be my hardware. It is Intel 2.6 Celron. I don't have money this month whatever.
If anyone has any ideas on how to stabilize my current setup that would help me a billion. Thx.

---

### Post by ibjsb4 on 2012-11-21
Try the usual fixes:

sudo apt-get update

sudo apt-get upgrade

sudo dpkg --configure -a

sudo apt-get install -f

Also take a look for alternate video drivers

Good luck

---

### Post by jbart0312 on 2012-11-21
I will try those. Thx

---

### Post by Bashing-om on 2012-11-21
nother thing, best that I recall the celeron boards only had 512 megs of ram initially.
check and see if you can add additional ram.
```
sudo dmidecode | less
```["q" to quit]
reveals lots of info.
[INDENT]my little bit <== BDQ

[/INDENT]

---

### Post by jbart0312 on 2012-12-01
> **Bashing-om said:**
> nother thing, best that I recall the celeron boards only had 512 megs of ram initially.
check and see if you can add additional ram.
```
sudo dmidecode | less
```["q" to quit]
reveals lots of info.[INDENT]my little bit <== BDQ

[/INDENT]
Hey...

What info specifically should I be watching for...

[PHP]
# dmidecode 2.11
SMBIOS 2.2 present.
34 structures occupying 876 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 19 bytes
BIOS Information
        Vendor: Phoenix Technologies, LTD
        Version: 6.00 PG
        Release Date: 12/08/2004
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 256 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 kB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
        Manufacturer:  
        Product Name:  
        Version:  
        Serial Number:  
        UUID: Not Present
        Wake-up Type: Other


Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
        Manufacturer:  
        Product Name: 845GV-ITE8712
        Version:  
        Serial Number:  

Handle 0x0003, DMI type 3, 13 bytes
Chassis Information
        Manufacturer:  
        Type: Desktop
        Lock: Not Present
        Version:  
        Serial Number:  
        Asset Tag:  
        Boot-up State: Unknown
        Power Supply State: Unknown
        Thermal State: Unknown
        Security Status: Unknown

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
        Socket Designation: Socket 478
        Type: Central Processor
        Family: Pentium II
        Manufacturer: Intel
        ID: 33 0F 00 00 FF FB EB BF
        Signature: Type 0, Family 15, Model 3, Stepping 3
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
        Version: Intel(R) Celeron(R) CPU
        Voltage: 0.0 V
        External Clock: 133 MHz
        Max Speed: 3066 MHz
        Current Speed: 2400 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0008
        L2 Cache Handle: 0x0009
        L3 Cache Handle: No L3 Cache

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
        Error Detecting Method: 8-bit Parity
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 2048 MB
        Supported Speeds:
                Other
        Supported Memory Types:
                Other
        Memory Module Voltage: 5.0 V
        Associated Memory Slots: 2
                0x0006
                0x0007
        Enabled Error Correcting Capabilities:
                None
Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0 1
        Current Speed: Unknown
        Type: Other
        Installed Size: 512 MB (Double-bank Connection)
        Enabled Size: 512 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2 3
        Current Speed: Unknown
        Type: Other
        Installed Size: 512 MB (Double-bank Connection)
        Enabled Size: 512 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Internal Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 kB
        Maximum Size: 32 kB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
        Speed: Unknown
        Error Correction Type: Unknown
        System Type: Unknown
        Associativity: Unknown

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
        Socket Designation: External Cache
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Back
        Location: External
        Installed Size: 256 kB
        Maximum Size: 256 kB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
 Speed: Unknown
        Error Correction Type: Unknown
        System Type: Unknown
        Associativity: Unknown

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: PRIMARY IDE
        Internal Connector Type: On Board IDE
        External Reference Designator:  
        External Connector Type: None
        Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SECONDARY IDE
        Internal Connector Type: On Board IDE
        External Reference Designator:  
        External Connector Type: None
        Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: FDD
        Internal Connector Type: On Board Floppy
        External Reference Designator:  
        External Connector Type: None
        Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: COM1
        Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
        External Reference Designator:  
        External Connector Type: DB-9 male
        Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: LPT1
        Internal Connector Type: DB-25 female
        External Reference Designator:  
        External Connector Type: DB-25 female
        Port Type: Parallel Port ECP/EPP

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
Port Connector Information
        Internal Reference Designator: Keyboard
        Internal Connector Type: PS/2
        External Reference Designator:  
        External Connector Type: PS/2
        Port Type: Keyboard Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: PS/2 Mouse
        Internal Connector Type: PS/2
        External Reference Designator:  
        External Connector Type: PS/2
        Port Type: Mouse Port

Handle 0x0011, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI0
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 1
        Characteristics:
                5.0 V is provided
                PME signal is supported

Handle 0x0012, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI1
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 2
        Characteristics:
                5.0 V is provided
                PME signal is supported

Handle 0x0013, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI2
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 3
        Characteristics:
                5.0 V is provided
                PME signal is supported
Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI3
        Type: 32-bit PCI
        Current Usage: In Use
        Length: Long
        ID: 4
        Characteristics:
                5.0 V is provided
                PME signal is supported

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
        Designation: AGP
        Type: 32-bit AGP
        Current Usage: Available
        Length: Long
        ID: 8
        Characteristics:
                5.0 V is provided

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB
        Internal Connector Type: None
        External Reference Designator:  
        External Connector Type: Other
        Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB
        Internal Connector Type: None
        External Reference Designator:  
        External Connector Type: Other
        Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB
        Internal Connector Type: None
        External Reference Designator:  
        External Connector Type: Other
        Port Type: USB
Handle 0x0019, DMI type 13, 22 bytes
BIOS Language Information
        Language Description Format: Long
        Installable Languages: 3
                n|US|iso8859-1
                n|US|iso8859-1
                r|CA|iso8859-1
        Currently Installed Language: n|US|iso8859-1

Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 2 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x001B, DMI type 17, 21 bytes
Memory Device
        Array Handle: 0x001A
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: SDRAM
        Type Detail: Synchronous

Handle 0x001C, DMI type 17, 21 bytes
Memory Device
        Array Handle: 0x001A
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: SDRAM
        Type Detail: Synchronous
Handle 0x001D, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 1 GB
        Physical Array Handle: 0x001A
        Partition Width: 1

Handle 0x001E, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0001FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x001B
        Memory Array Mapped Address Handle: 0x001D
        Partition Row Position: 1

Handle 0x001F, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00020000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x001C
        Memory Array Mapped Address Handle: 0x001D
        Partition Row Position: 1

Handle 0x0020, DMI type 32, 11 bytes
System Boot Information
        Status: No errors detected

Handle 0x0021, DMI type 127, 4 bytes
End Of Table


[/PHP]
I just spent all day reinstalling Lubuntu all over again\  the system froze and I pulled the plug. My grub directory was erased. LOL. 

My system froze again 15 minutes ago but this time I used a method a found 

alt + Prt Scr SysRq ..  R.. E.. I.. S.. U.. B

I thought I was saving myself some money when I picked up this build with the Celron 2.4 Ghz processor thinking that would be enough to surf the web, blog and youtube but the only distro of Ubuntu that the hardware likes is Lubuntu. I had Slax going earlier today. Boy, that one is filled with holes. I may need more RAM and find some fix that will stabilize the graphical interface...

Still looking for answers...

---

### Post by ohnonot on 2012-12-01
> **jbart0312 said:**
> 
Still looking for answers...
i just tried dmidecode on my own machine - the output for "memory device" is towards the end - and with | less you have to scroll down to see it.

but i would try to install hardinfo really. seems you will need more info on your hardware anyway.

if your machine is physically healthy then it's definitely enough to surf the web and install and run any flavor of ubuntu (not unity, though).
but lubuntu is a good choice in my opinion.

btw, it sounds you have an onboard graphics card there.
what was it, intel?

don't give up on old hardware!

edit: just noticed that you posted the complete output. yes, 512MB of RAM. i didn't see anything about a graphic card though.

---

### Post by jbart0312 on 2012-12-01
> **ohnonot said:**
> i just tried dmidecode on my own machine - the output for "memory device" is towards the end - and with | less you have to scroll down to see it.

but i would try to install hardinfo really. seems you will need more info on your hardware anyway.

if your machine is physically healthy then it's definitely enough to surf the web and install and run any flavor of ubuntu (not unity, though).
but lubuntu is a good choice in my opinion.

btw, it sounds you have an onboard graphics card there.
what was it, intel?

don't give up on old hardware!

edit: just noticed that you posted the complete output. yes, 512MB of RAM. i didn't see anything about a graphic card though.

Hey.

Thx for the reply!

Yea, I did see the output memory device. What I gathered from dmidecode is that my system supports 2gb RAM. I am not smart enough to interpret dmidecode output but I am pretty sure when taking a look at sysinfo that I am running half that at the current moment. Or is it just 512. I dont know. dmidecode shows 512 at four different entries.

**I'm editing this post**:

[PHP]Handle 0x001E, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0001FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x001B
        Memory Array Mapped Address Handle: 0x001D
        Partition Row Position: 1

Handle 0x001F, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00020000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 512 MB
        Physical Device Handle: 0x001C
        Memory Array Mapped Address Handle: 0x001D
        Partition Row Position: 1[/PHP]**Is this the RAM??**

I am gonna chk up on your suggestion hardinfo. Is that a package?

Not gonna give up on this machine. Why would I? If I cannot configure an older build then what point is there in an upgrade! Ha!

And yes. Onboard graphics. Sysinfo isnt showing much info this time around. Maybe that's why I need this hardinfo installation.

And yea also to Lubuntu. I like it. At first I tried the regular installation of Ubuntu but the graphic problem wouldn't allow it to run properly on this machine. After further research I learned that Lubuntu doesnt use the same graphic rendering or something along those lines. In any case, Lubuntu is the best choice for me right now.

The graphics are still acting funny on my machine, even as I was responding things were not acting properly!

---

### Post by ohnonot on 2012-12-02
lubuntu - that should be using synaptic.
you just find hardinfo from there and install it. yes, it's a package.

i did not *study* the dmidecode output but my guess is that your machine has 4 slots for ram, each of which is capable of managing 512MB of ram, but only one of them has a ram chip inserted.
really, open the machine and have a look!
also, for an older machine these ram chips are quite cheap.
same goes for the graphic card - it shouldn't be expensive to get sth that is *way *better than a 5+ys old intel onboard chip. and the slots should be just there if it's a non-laptop.

but i'm still concerned about the physical health of your machine - what you describe should not be happening.
were you able to define the problem more?

---

### Post by Bashing-om on 2012-12-02
jbart0312;
dmidecode confirms celeron processor, 2 of 4 banks of 512 megs of ram, Per system requirements, celeron chip just not hoss enough to run ubuntu, specs should run lubuntu screaming !
Now I must point out something I find disturbing: dmidecode ->
version: Intel(R) celeron(R) CPU
Voltage 0.0 V

On a stable machine I have always observed a positive value for a voltage (draw). This in  my mind warrants further investigation, The hardwareinfo package may help.
[INDENT]my 1 pound worth <== BDQ
 
[/INDENT]

---

### Post by jbart0312 on 2012-12-02
Well,

Hardinfo summarized memory shows 1017 (328 used)

I feel that the graphics card and memory stick recommendations are the next step.

The machine actually is booting rather well right now.

One positive from this experience is that I dived head first into my recent install with a Lubuntu Live USB and a totally fresh re-format of my hard drive. I gave the drive two partitions, including a second 4Gb partition formatted for swap. The main partition is formatted ext4. So, hopefully, sooner than later, I can open the case and install more RAM and a dedicated graphics card. 

Hardinfo shows good marks for the actual processor. It's running at 2394 Mghz. The benchmark tests have another value for something desribed as Power PC 740/750 (280.00 Mghz), not really sure what that is but it scored very low.

As long as I can avoid a "*pulling the plug*" scenario again, until upgrade, things are good!

(Not sure about the Vltage reading equaling zero.)

Thank sincerely for the responses to my post/ /

I don't have superior tech knowledge in the field but I can find my way around.

I am in the middle of reading this book;

**The Art of Unix Programming** by* Eric Steven Raymond*

It's quite good!

If anyone has more good suggestions or ways to strengthen my OS temporarily until I upgrade the RAM I would love to hear them. I think if I avoid overloading the desktop with too many processes at one time then it shouldn't crash.

(edit) One last point that I forgot to mention was why my system originally froze and erased my /GRUB directory. It happened when I left my desktop running overnight. The next day when I sat down and wiggled the mouse to bring my monitor out of sleep mode the monitor refreshed itself but the rest of my services were completely frozen. I pulled the plug and experienced the unfortunate. The computer rebooted to a screen relaying some info with a prompt grub>. However, this wasn't really a terminal (I guess), because sudo wasn't recognized. Neither were most of the commands I know that talk to ubuntu. I rebooted the machine into Win XP and checked the Ubuntu folder shortly realizing that the grub directory was empty. The original installation came from inside the windows environment using Wubi.

---

### Post by ohnonot on 2012-12-03
windows doesn't like being shut down too hard.
there's actually quite many things can go wrong with windows;

if you were running lubuntu from within windows (iirc that's what wubi does) i'm not surprised you were having problems.

if you're hardware is healthy, with these specs you should be running lubuntu just fine, no need to upgrade any hardware!
i've been running lubuntu with 512mb ram and a 1.3GHz processor,no problem.

i recommend to:
_first:_    install windows on the first partition of the first hd (if you feel you need it).
_second:_  install lubuntu in the free space. i don't know about linux and swap, but i never ever saw any kind of linux using more than 10% rams worth of swap space. in my opinion, 1gig of swap is plenty in your case.

---

### Post by Bashing-om on 2012-12-03
Sounds like everything is rosy ! 

My experience-> many faceted operating system, only limitation is one's own imagination and willingness to think.

Learning: follow your curiosity !

[INDENT][INDENT]happy 'buntu'n < == BDQ

[/INDENT][/INDENT]

---

