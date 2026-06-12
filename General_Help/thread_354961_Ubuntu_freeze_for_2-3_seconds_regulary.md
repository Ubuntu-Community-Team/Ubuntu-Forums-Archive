---
title: "Ubuntu freeze for 2-3 seconds regulary"
date: 2007-02-06
forum: General Help
---

### Post by ZoRaC on 2007-02-06
Hi all!

I'm having 2-3 seconds freezes on a regular basis, approx. every other minute.
I think it might have something to do with my network config, this is from the syslog:
> Feb  6 23:13:24 zorac-ubuntu kernel: [17182212.196000] hdb: status timeout: status=0xd0 { Busy }
Feb  6 23:13:24 zorac-ubuntu kernel: [17182212.196000] ide: failed opcode was: unknown
Feb  6 23:13:24 zorac-ubuntu kernel: [17182212.244000] hdb: ATAPI reset complete
Feb  6 23:13:29 zorac-ubuntu dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Feb  6 23:13:58 zorac-ubuntu last message repeated 2 times
Feb  6 23:13:58 zorac-ubuntu kernel: [17182246.148000] hdb: status timeout: status=0xd0 { Busy }
Feb  6 23:13:58 zorac-ubuntu kernel: [17182246.148000] ide: failed opcode was: unknown
Feb  6 23:13:58 zorac-ubuntu kernel: [17182246.196000] hdb: ATAPI reset complete
Feb  6 23:14:14 zorac-ubuntu dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Feb  6 23:14:52 zorac-ubuntu last message repeated 3 times
Feb  6 23:16:00 zorac-ubuntu last message repeated 5 times
Feb  6 23:16:44 zorac-ubuntu last message repeated 3 times
Feb  6 23:16:54 zorac-ubuntu kernel: [17182422.780000] hdb: status timeout: status=0xd0 { Busy }
Feb  6 23:16:54 zorac-ubuntu kernel: [17182422.780000] ide: failed opcode was: unknown
Feb  6 23:16:55 zorac-ubuntu kernel: [17182422.828000] hdb: ATAPI reset complete

Anyone have any clue?
Let me know if you need more information. :)

---

### Post by hanzomon4 on 2007-02-06
What happens if you reboot?
Check the system monitor to see how much swap space you have,,,,,,,,,

---

### Post by ZoRaC on 2007-02-06
I've tried rebooting, no change... :(
Using 0% swap and 40% memory ATM....

---

### Post by bettlebrox on 2007-02-06
I'd say the problem is hdb. Is hdb a harddrive or an optical drive? Methinks a bad CD drive or a dirty disk.

---

### Post by WinterWeaver on 2007-02-06
Are you running Azureus, or another torrent downloader?

this happened to me with Azureus, and I have a buddy using uTorrent with Windoze, with the same problem also.

The periodic freezing will stop once the donwloads are finished (that's of course if this is the problem)

... just a thought on what it may be....

Hope it help... ^_^

WW

---

### Post by ZoRaC on 2007-02-07
> **bettlebrox said:**
> I'd say the problem is hdb. Is hdb a harddrive or an optical drive? Methinks a bad CD drive or a dirty disk.

I feel almost n00bish, but how do I check what hdb is? :roll: 
I tried mounting it, I think :P, but wasn't able to access it.

I't a laptop with only 1 HD, so it can't be that... :)

WinterWeaver:
Nom I'm not using such software. :)

---

### Post by Rich78 on 2007-02-07
Do you have a CD/DVD in the drive?  If so take it out and see if it rectifies the problem.

---

### Post by ZoRaC on 2007-02-07
> **Rich78 said:**
> Do you have a CD/DVD in the drive?  If so take it out and see if it rectifies the problem.

Nope, the drive is empty...

---

### Post by hanzomon4 on 2007-02-07
Check how much swap space you have, I have 1.4gb of swap space. 
I recently had a problem with my swap partition not activating and this caused my system to slow to a crawl.

---

### Post by bettlebrox on 2007-02-07
> **ZoRaC said:**
> I feel almost n00bish, but how do I check what hdb is? :roll: 

grep hdb /etc/fstab

---

### Post by ZoRaC on 2007-02-09
> **bettlebrox said:**
> grep hdb /etc/fstab

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

So it seems it's my DVD-writer that's causing this, but why is Ubuntu trying to read it on a regular basis and why does it cause the system to freeze? 
Could it be that it's not set up with DMA?

---

### Post by bettlebrox on 2007-02-10
>Could it be that it's not set up with DMA?
I don't think, not using DMA would cause that problem, but  to check if dma is enabled or not do this:

sudo hdparm   /dev/hdb

If DMA is off you can enable it with:

sudo hdparm -d 1 /dev/hdb

-d 0 will disable DMA. 

If you do have to enable DMA test things for a while to make sure things aren't worse. U'll need to edit /etc/hdparm.conf to have it set DMA on reboots.

If it's not DMA, then maybe you have a CD-player program or applet running that keeps trying to access the drive every few seconds? U can use the command lsof to find out what is using the device:

sudo lsof /dev/hdb

Luck
Mick

---

### Post by ZoRaC on 2007-02-10
Thanks for the instructions, DMA was disabled on hdb, but enabeling it didn't make any difference.
I also tried to disable eth0 in the "network"-GUI, since the syslog was full of DHCP-attempts for it, but that didn't help either.

Any other suggestions?

Edit:
BTW, the "sudo lsof /dev/hdb" came up with nothing...

---

### Post by bettlebrox on 2007-02-10
Which kernel version are you using? (The command "uname -a" will tell you.)
Which version of Ubuntu are you using?
What kind of processor do you have? (The output of "cat /proc/cpuinfo" will tell you.)

Upgrading or changing kernel version might help, and another option is that the IDE cable on the drive is loose. U comfortable opening up your system and making sure the cables are secure?

---

### Post by ZoRaC on 2007-02-10
1: 2.6.17-11-generic, but I just upgraded from 2.6.17.10 two hours ago, but it didn't help.
2: I belive it's 6.10
3:> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.40GHz
stepping        : 8
cpu MHz         : 1396.683
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
bogomips        : 2797.62

It's a laptop, so there arn't any cables to check, but both the harddrive and DVD-writer are firmly in place, and are working fine in Windows.

---

### Post by bettlebrox on 2007-02-12
Whats the output of lspci? Might be able to see what kind of drive it is & google to see if anyone else has had the same or similar problems.

---

### Post by Hallvor on 2007-02-12
I have the same problem. Freezes of 2-3 seconds every 20 minutes. Annoying if watching a movie. Never had the problem in Windows, btw.

Output of lspci

> hallvor@hallvor-desktop:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:07.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:02:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

Output of uname -a

> Linux hallvor-desktop 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux

Edit: Cpuinfo

> hallvor@hallvor-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2500+
stepping        : 0
cpu MHz         : 1830.220
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3664.14


DMA is enabled.

Could the problem be caused by my ntfs-3g driver? because I use aMule to read/write to a shared drive (with Windows XP).

ZoRaC: Are you using ntfs-3g?

---

### Post by ZoRaC on 2007-02-13
Here is my lspci:> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

I'v never heard of ntfs-3g, so I'm probably not using it :P

---

### Post by Hallvor on 2007-02-13
Probably not. Should have tested with an ethernet connection to see if it is a wireless issue.

---

### Post by bettlebrox on 2007-02-13
I am at a loss, and lspci doesn't say what the drives are ... duh! ;)


ZoRaC, try this:

dmesg |grep hdb

Or "dmesg |more" and look at the output and see if ID's your drive. What model laptop is it?

Hallvor, you can try dmesg and replce hdb with whatever your drive is. Also, try upgrading your kernel is see it solves your problems, also what model laptop is it (if it's a laptop)?

---

### Post by bettlebrox on 2007-02-13
After a whole bunch of googling, it looks this problem is *usually* cause by certain buggy firmware either in the optical drive on the bus it's connected too. Probably the best thing at the moment is to disable DMA.

If we can figure out what the drive is then that might help hunt down the cause.

---

### Post by dcstar on 2007-02-13
> **Hallvor said:**
> I have the same problem. Freezes of 2-3 seconds every 20 minutes. Annoying if watching a movie. Never had the problem in Windows, btw.
......

Personally, if I had a AMD CPU I would be using at least a 686 kernel, and preferably the K7 one.

---

### Post by Hallvor on 2007-02-14
OK, here it is.


> hallvor@hallvor-desktop:~$ dmesg |more
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b50
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff79c0
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1830.220 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.216000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.216000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.228000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
[17179569.228000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.308000] Calibrating delay using timer specific routine.. 3664.14 BogoMIPS (lpj=7328298)
[17179569.308000] Security Framework v1.0.0 initialized
[17179569.308000] SELinux:  Disabled at boot.
[17179569.308000] Mount-cache hash table entries: 512
[17179569.308000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000
00000000 00000000 00000000 00000000
[17179569.308000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.308000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.308000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.308000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.308000] mtrr: v2.0 (20020519)
[17179569.308000] CPU: AMD Athlon(tm) XP 2500+ stepping 00
[17179569.308000] Enabling fast FPU save and restore... done.
[17179569.308000] Enabling unmasked SIMD FPU exception support... done.
[17179569.308000] Checking 'hlt' instruction... OK.
[17179569.324000] checking if image is initramfs... it is
[17179569.884000] Freeing initrd memory: 6617k freed
[17179569.900000] ACPI: Looking for DSDT ... not found!
[17179569.912000] ENABLING IO-APIC IRQs
[17179569.912000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.056000] NET: Registered protocol family 16
[17179570.056000] EISA bus registered
[17179570.056000] ACPI: bus type pci registered
[17179570.056000] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[17179570.056000] PCI: Using configuration type 1
[17179570.056000] ACPI: Subsystem revision 20051216
[17179570.060000] ACPI: Interpreter enabled
[17179570.060000] ACPI: Using IOAPIC for interrupt routing
[17179570.060000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.060000] PCI: Probing PCI hardware (bus 00)
[17179570.064000] PCI: nForce2 C1 Halt Disconnect fixup
[17179570.064000] Boot video device is 0000:02:00.0
[17179570.064000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179570.136000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179570.152000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.152000] pnp: PnP ACPI init
[17179570.160000] pnp: PnP ACPI: found 14 devices
[17179570.160000] PnPBIOS: Disabled by ACPI PNP
[17179570.160000] PCI: Using ACPI for IRQ routing
[17179570.160000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.200000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[17179570.200000] PCI: Bridge: 0000:00:08.0
[17179570.200000]   IO window: disabled.
[17179570.200000]   MEM window: ea000000-eaffffff
[17179570.200000]   PREFETCH window: disabled.
[17179570.200000] PCI: Bridge: 0000:00:1e.0
[17179570.200000]   IO window: c000-cfff
[17179570.200000]   MEM window: e8000000-e9ffffff
[17179570.200000]   PREFETCH window: c0000000-dfffffff
[17179570.200000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179570.200000] audit: initializing netlink socket (disabled)
[17179570.200000] audit(1171314349.200:1): initialized
[17179570.200000] VFS: Disk quotas dquot_6.5.1
[17179570.200000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.200000] Initializing Cryptographic API
[17179570.200000] io scheduler noop registered
[17179570.200000] io scheduler anticipatory registered
[17179570.200000] io scheduler deadline registered
[17179570.200000] io scheduler cfq registered
[17179570.200000] isapnp: Scanning for PnP cards...
[17179570.560000] isapnp: No Plug & Play device found
[17179570.572000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64
irq 1,12
[17179570.576000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.576000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.576000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.576000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.580000] mice: PS/2 mouse device common for all mice
[17179570.580000] EISA: Probing bus 0 at eisa.0
[17179570.580000] Cannot allocate resource for EISA slot 4
[17179570.580000] Cannot allocate resource for EISA slot 5
[17179570.580000] EISA: Detected 0 cards.
[17179570.580000] NET: Registered protocol family 2
[17179570.612000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.620000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.620000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP: Hash tables configured (established 32768 bind 32768)
[17179570.620000] TCP reno registered
[17179570.620000] TCP bic registered
[17179570.620000] NET: Registered protocol family 1
[17179570.620000] NET: Registered protocol family 8
[17179570.620000] NET: Registered protocol family 20
[17179570.620000] Using IPI Shortcut mode
[17179570.620000] ACPI wakeup devices:
[17179570.620000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179570.620000] ACPI: (supports S0 S1 S4 S5)
[17179570.620000] Freeing unused kernel memory: 288k freed
[17179570.664000] vga16fb: initializing
[17179570.664000] vga16fb: mapped to 0xc00a0000
[17179570.800000] Console: switching to colour frame buffer device 80x25
[17179570.800000] fb0: VGA16 VGA frame buffer device
[17179571.816000] Capability LSM initialized
[17179571.980000] ACPI: Fan [FAN] (on)
[17179571.988000] ACPI: Thermal Zone [THRM] (51 C)
[17179572.432000] SCSI subsystem initialized
[17179572.436000] ACPI: bus type scsi registered
[17179572.436000] libata version 1.20 loaded.
[17179572.436000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179572.436000] NFORCE2: chipset revision 162
[17179572.436000] NFORCE2: not 100% native mode: will probe irqs later
[17179572.436000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179572.436000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179572.436000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179572.436000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.436000] Probing IDE interface ide0...
[17179572.952000] hdb: Maxtor 6Y120P0, ATA DISK drive
[17179573.008000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.008000] Probing IDE interface ide1...
[17179573.296000] hdc: IBM-DTTA-371010, ATA DISK drive
[17179573.744000] hdd: DVDRW 16X16, ATAPI CD/DVD-ROM drive
[17179573.800000] ide1 at 0x170-0x177,0x376 on irq 15
[17179573.828000] hdb: max request size: 128KiB
[17179573.836000] hdb: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(33)
[17179573.836000] hdb: cache flushes supported
[17179573.836000]  hdb: hdb1 hdb2 < hdb5 >
[17179573.856000] hdc: max request size: 128KiB
[17179573.860000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179573.860000] Uniform CD-ROM driver Revision: 3.20
[17179573.868000] hdc: 19746720 sectors (10110 MB) w/465KiB Cache, CHS=19590/16/63, UDMA(33)
[17179573.868000] hdc: cache flushes not supported
[17179573.868000]  hdc: hdc1 hdc2 < hdc5 >
[17179574.232000] usbcore: registered new driver usbfs
[17179574.232000] usbcore: registered new driver hub
[17179574.236000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI)
Driver (PCI)
[17179574.236000] **** SET: Misaligned resource pointer: de840c02 Type 07 Len 0
[17179574.236000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179574.236000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 177
[17179574.236000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179574.236000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179574.236000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179574.236000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xeb003000
[17179574.292000] hub 1-0:1.0: USB hub found
[17179574.292000] hub 1-0:1.0: 3 ports detected
[17179574.396000] **** SET: Misaligned resource pointer: de840902 Type 07 Len 0
[17179574.396000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179574.396000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 185
[17179574.396000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179574.396000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179574.396000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179574.396000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xeb004000
[17179574.452000] hub 2-0:1.0: USB hub found
[17179574.452000] hub 2-0:1.0: 3 ports detected
[17179574.556000] **** SET: Misaligned resource pointer: de840602 Type 07 Len 0
[17179574.556000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179574.556000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 193
[17179574.556000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179574.556000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179574.556000] ehci_hcd 0000:00:02.2: debug port 1
[17179574.556000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179574.556000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179574.556000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xeb005000
[17179574.556000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.556000] hub 3-0:1.0: USB hub found
[17179574.556000] hub 3-0:1.0: 6 ports detected
[17179574.744000] Attempting manual resume
[17179574.756000] kjournald starting.  Commit interval 5 seconds
[17179574.756000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.588000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.596000] agpgart: Detected NVIDIA nForce2 chipset
[17179590.604000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179590.964000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179590.964000] **** SET: Misaligned resource pointer: dfdc6622 Type 07 Len 0
[17179590.964000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179590.964000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 177
[17179590.964000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179591.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.304000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179591.304000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179591.476000] Floppy drive(s): fd0 is 1.44M
[17179591.484000] eth0: forcedeth.c: subsystem: 0147b:1c02 bound to 0000:00:04.0[17179591.484000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.496000] FDC 0 is a post-1991 82077
[17179591.524000] **** SET: Misaligned resource pointer: daf09aa2 Type 07 Len 0
[17179591.524000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[17179591.524000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 185
[17179591.524000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179591.548000] parport: PnPBIOS parport detected.
[17179591.548000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.656000] Real Time Clock Driver v1.12
[17179591.752000] input: PC Speaker as /class/input/input1
[17179591.844000] intel8x0_measure_ac97_clock: measured 52430 usecs
[17179591.844000] intel8x0: clocking to 47484
[17179592.020000] **** SET: Misaligned resource pointer: da8528c2 Type 07 Len 0
[17179592.020000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179592.020000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179592.020000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[17179592.264000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179592.292000] ts: Compaq touchscreen protocol output
[17179592.848000] lp0: using parport0 (interrupt-driven).
[17179593.040000] fuse init (API version 7.3)
[17179593.092000] Adding 441748k swap on /dev/hdc5.  Priority:-1 extents:1 across:441748k
[17179593.252000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179593.252000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 13 13 12 12  dBm
Maximum
[17179593.288000] EXT3 FS on hdc1, internal journal
[17179593.484000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.484000] md: bitmap version 4.39
[17179594.268000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179594.464000] NET: Registered protocol family 17
[17179595.172000] cdrom: open failed.
[17179606.860000] ACPI: Power Button (FF) [PWRF]
[17179606.860000] ACPI: Power Button (CM) [PWRB]
[17179606.988000] ibm_acpi: ec object not found
[17179607.028000] pcc_acpi: loading...
[17179611.896000] eth0: no link during initialization.
[17179618.100000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179618.100000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179618.100000] [fglrx] module loaded - fglrx 8.33.6 [Jan  8 2007] on minor 0
[17179618.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179622.152000] ppdev: user-space parallel port driver
[17179622.372000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179622.372000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179622.372000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17179622.372000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179622.372000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179622.372000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179622.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179622.380000] [fglrx] total      GART = 134217728
[17179622.380000] [fglrx] free       GART = 118222848
[17179622.380000] [fglrx] max single GART = 118222848
[17179622.384000] [fglrx] total      LFB  = 134217728
[17179622.384000] [fglrx] free       LFB  = 116387840
[17179622.384000] [fglrx] max single LFB  = 116387840
[17179622.384000] [fglrx] total      Inv  = 0
[17179622.384000] [fglrx] free       Inv  = 0
[17179622.384000] [fglrx] max single Inv  = 0
[17179622.384000] [fglrx] total      TIM  = 0
[17179622.856000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179622.856000] apm: overridden by ACPI.
[17179623.392000] ip_tables: (C) 2000-2002 Netfilter core team
[17179623.508000] Netfilter messages via NETLINK v0.30.
[17179623.568000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
[17179626.228000] Bluetooth: Core ver 2.8
[17179626.228000] NET: Registered protocol family 31
[17179626.228000] Bluetooth: HCI device and connection manager initialized
[17179626.228000] Bluetooth: HCI socket layer initialized
[17179626.328000] Bluetooth: L2CAP ver 2.8
[17179626.328000] Bluetooth: L2CAP socket layer initialized
[17179626.388000] Bluetooth: RFCOMM socket layer initialized
[17179626.388000] Bluetooth: RFCOMM TTY layer initialized
[17179626.388000] Bluetooth: RFCOMM ver 1.7
[17186983.228000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63298 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=59140 RES=0x00 ACK URGP=0
[17186997.992000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63892 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=65340 RES=0x00 ACK URGP=0
[17211189.460000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=222.212.170.145 DST=192.168.1.135 LEN=1454 TOS=0x00 PREC=0x00 TTL=108 ID=5354 DF PROTO=TCP SPT=6253 DPT=40152 WINDOW=64270 RES=0x00 ACK PSH URGP=0
[17231731.860000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=19558 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231736.868000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20028 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231746.836000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20881 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231764.552000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=22403 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK URGP=0
[17231766.900000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=22608 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK PSH URGP=0
[17231804.976000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=26000 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=65535 RES=0x00 ACK URGP=0
[17247631.392000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1)
[17247631.392000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xc8bfbae0 still mapped (user_handle = 0x00013000)
[17247631.400000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1), force it to be removed anyway
[17247631.408000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17306607.340000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17306608.304000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17306608.388000] NTFS volume version 3.1.
[17306844.692000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17306848.100000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17306848.100000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17306848.100000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17306848.100000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17306848.100000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17306848.100000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17306848.100000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17306848.112000] [fglrx] total      GART = 134217728
[17306848.112000] [fglrx] free       GART = 118222848
[17306848.112000] [fglrx] max single GART = 118222848
[17306848.112000] [fglrx] total      LFB  = 134217728
[17306848.112000] [fglrx] free       LFB  = 116387840
[17306848.112000] [fglrx] max single LFB  = 116387840
[17306848.112000] [fglrx] total      Inv  = 0
[17306848.112000] [fglrx] free       Inv  = 0
[17306848.112000] [fglrx] max single Inv  = 0
[17306848.112000] [fglrx] total      TIM  = 0

---

### Post by Hallvor on 2007-02-14
This is the output of my primary drive. 

> hallvor@hallvor-desktop:~$ dmesg /dev/hdc1
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b50
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff79c0
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1830.220 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.216000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.216000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.228000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
[17179569.228000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.308000] Calibrating delay using timer specific routine.. 3664.14 BogoMIPS (lpj=7328298)
[17179569.308000] Security Framework v1.0.0 initialized
[17179569.308000] SELinux:  Disabled at boot.
[17179569.308000] Mount-cache hash table entries: 512
[17179569.308000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.308000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.308000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.308000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.308000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.308000] mtrr: v2.0 (20020519)
[17179569.308000] CPU: AMD Athlon(tm) XP 2500+ stepping 00
[17179569.308000] Enabling fast FPU save and restore... done.
[17179569.308000] Enabling unmasked SIMD FPU exception support... done.
[17179569.308000] Checking 'hlt' instruction... OK.
[17179569.324000] checking if image is initramfs... it is
[17179569.884000] Freeing initrd memory: 6617k freed
[17179569.900000] ACPI: Looking for DSDT ... not found!
[17179569.912000] ENABLING IO-APIC IRQs
[17179569.912000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.056000] NET: Registered protocol family 16
[17179570.056000] EISA bus registered
[17179570.056000] ACPI: bus type pci registered
[17179570.056000] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[17179570.056000] PCI: Using configuration type 1
[17179570.056000] ACPI: Subsystem revision 20051216
[17179570.060000] ACPI: Interpreter enabled
[17179570.060000] ACPI: Using IOAPIC for interrupt routing
[17179570.060000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.060000] PCI: Probing PCI hardware (bus 00)
[17179570.064000] PCI: nForce2 C1 Halt Disconnect fixup
[17179570.064000] Boot video device is 0000:02:00.0
[17179570.064000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179570.136000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179570.152000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.152000] pnp: PnP ACPI init
[17179570.160000] pnp: PnP ACPI: found 14 devices
[17179570.160000] PnPBIOS: Disabled by ACPI PNP
[17179570.160000] PCI: Using ACPI for IRQ routing
[17179570.160000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.200000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[17179570.200000] PCI: Bridge: 0000:00:08.0
[17179570.200000]   IO window: disabled.
[17179570.200000]   MEM window: ea000000-eaffffff
[17179570.200000]   PREFETCH window: disabled.
[17179570.200000] PCI: Bridge: 0000:00:1e.0
[17179570.200000]   IO window: c000-cfff
[17179570.200000]   MEM window: e8000000-e9ffffff
[17179570.200000]   PREFETCH window: c0000000-dfffffff
[17179570.200000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179570.200000] audit: initializing netlink socket (disabled)
[17179570.200000] audit(1171314349.200:1): initialized
[17179570.200000] VFS: Disk quotas dquot_6.5.1
[17179570.200000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.200000] Initializing Cryptographic API
[17179570.200000] io scheduler noop registered
[17179570.200000] io scheduler anticipatory registered
[17179570.200000] io scheduler deadline registered
[17179570.200000] io scheduler cfq registered
[17179570.200000] isapnp: Scanning for PnP cards...
[17179570.560000] isapnp: No Plug & Play device found
[17179570.572000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.576000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.576000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.576000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.576000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.580000] mice: PS/2 mouse device common for all mice
[17179570.580000] EISA: Probing bus 0 at eisa.0
[17179570.580000] Cannot allocate resource for EISA slot 4
[17179570.580000] Cannot allocate resource for EISA slot 5
[17179570.580000] EISA: Detected 0 cards.
[17179570.580000] NET: Registered protocol family 2
[17179570.612000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.620000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.620000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP: Hash tables configured (established 32768 bind 32768)
[17179570.620000] TCP reno registered
[17179570.620000] TCP bic registered
[17179570.620000] NET: Registered protocol family 1
[17179570.620000] NET: Registered protocol family 8
[17179570.620000] NET: Registered protocol family 20
[17179570.620000] Using IPI Shortcut mode
[17179570.620000] ACPI wakeup devices:
[17179570.620000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179570.620000] ACPI: (supports S0 S1 S4 S5)
[17179570.620000] Freeing unused kernel memory: 288k freed
[17179570.664000] vga16fb: initializing
[17179570.664000] vga16fb: mapped to 0xc00a0000
[17179570.800000] Console: switching to colour frame buffer device 80x25
[17179570.800000] fb0: VGA16 VGA frame buffer device
[17179571.816000] Capability LSM initialized
[17179571.980000] ACPI: Fan [FAN] (on)
[17179571.988000] ACPI: Thermal Zone [THRM] (51 C)
[17179572.432000] SCSI subsystem initialized
[17179572.436000] ACPI: bus type scsi registered
[17179572.436000] libata version 1.20 loaded.
[17179572.436000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179572.436000] NFORCE2: chipset revision 162
[17179572.436000] NFORCE2: not 100% native mode: will probe irqs later
[17179572.436000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179572.436000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179572.436000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179572.436000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.436000] Probing IDE interface ide0...
[17179572.952000] hdb: Maxtor 6Y120P0, ATA DISK drive
[17179573.008000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.008000] Probing IDE interface ide1...
[17179573.296000] hdc: IBM-DTTA-371010, ATA DISK drive
[17179573.744000] hdd: DVDRW 16X16, ATAPI CD/DVD-ROM drive
[17179573.800000] ide1 at 0x170-0x177,0x376 on irq 15
[17179573.828000] hdb: max request size: 128KiB
[17179573.836000] hdb: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(33)
[17179573.836000] hdb: cache flushes supported
[17179573.836000]  hdb: hdb1 hdb2 < hdb5 >
[17179573.856000] hdc: max request size: 128KiB
[17179573.860000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179573.860000] Uniform CD-ROM driver Revision: 3.20
[17179573.868000] hdc: 19746720 sectors (10110 MB) w/465KiB Cache, CHS=19590/16/63, UDMA(33)
[17179573.868000] hdc: cache flushes not supported
[17179573.868000]  hdc: hdc1 hdc2 < hdc5 >
[17179574.232000] usbcore: registered new driver usbfs
[17179574.232000] usbcore: registered new driver hub
[17179574.236000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179574.236000] **** SET: Misaligned resource pointer: de840c02 Type 07 Len 0
[17179574.236000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179574.236000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 177
[17179574.236000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179574.236000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179574.236000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179574.236000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xeb003000
[17179574.292000] hub 1-0:1.0: USB hub found
[17179574.292000] hub 1-0:1.0: 3 ports detected
[17179574.396000] **** SET: Misaligned resource pointer: de840902 Type 07 Len 0
[17179574.396000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179574.396000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 185
[17179574.396000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179574.396000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179574.396000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179574.396000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xeb004000
[17179574.452000] hub 2-0:1.0: USB hub found
[17179574.452000] hub 2-0:1.0: 3 ports detected
[17179574.556000] **** SET: Misaligned resource pointer: de840602 Type 07 Len 0
[17179574.556000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179574.556000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 193
[17179574.556000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179574.556000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179574.556000] ehci_hcd 0000:00:02.2: debug port 1
[17179574.556000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179574.556000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179574.556000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xeb005000
[17179574.556000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.556000] hub 3-0:1.0: USB hub found
[17179574.556000] hub 3-0:1.0: 6 ports detected
[17179574.744000] Attempting manual resume
[17179574.756000] kjournald starting.  Commit interval 5 seconds
[17179574.756000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.588000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.596000] agpgart: Detected NVIDIA nForce2 chipset
[17179590.604000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179590.964000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179590.964000] **** SET: Misaligned resource pointer: dfdc6622 Type 07 Len 0
[17179590.964000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179590.964000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 177
[17179590.964000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179591.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.304000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179591.304000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179591.476000] Floppy drive(s): fd0 is 1.44M
[17179591.484000] eth0: forcedeth.c: subsystem: 0147b:1c02 bound to 0000:00:04.0[17179591.484000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.496000] FDC 0 is a post-1991 82077
[17179591.524000] **** SET: Misaligned resource pointer: daf09aa2 Type 07 Len 0
[17179591.524000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[17179591.524000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 185
[17179591.524000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179591.548000] parport: PnPBIOS parport detected.
[17179591.548000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.656000] Real Time Clock Driver v1.12
[17179591.752000] input: PC Speaker as /class/input/input1
[17179591.844000] intel8x0_measure_ac97_clock: measured 52430 usecs
[17179591.844000] intel8x0: clocking to 47484
[17179592.020000] **** SET: Misaligned resource pointer: da8528c2 Type 07 Len 0
[17179592.020000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179592.020000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179592.020000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[17179592.264000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179592.292000] ts: Compaq touchscreen protocol output
[17179592.848000] lp0: using parport0 (interrupt-driven).
[17179593.040000] fuse init (API version 7.3)
[17179593.092000] Adding 441748k swap on /dev/hdc5.  Priority:-1 extents:1 across:441748k
[17179593.252000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179593.252000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 13 13 12 12  dBm Maximum
[17179593.288000] EXT3 FS on hdc1, internal journal
[17179593.484000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.484000] md: bitmap version 4.39
[17179594.268000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179594.464000] NET: Registered protocol family 17
[17179595.172000] cdrom: open failed.
[17179606.860000] ACPI: Power Button (FF) [PWRF]
[17179606.860000] ACPI: Power Button (CM) [PWRB]
[17179606.988000] ibm_acpi: ec object not found
[17179607.028000] pcc_acpi: loading...
[17179611.896000] eth0: no link during initialization.
[17179618.100000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179618.100000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179618.100000] [fglrx] module loaded - fglrx 8.33.6 [Jan  8 2007] on minor 0
[17179618.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179622.152000] ppdev: user-space parallel port driver
[17179622.372000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179622.372000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179622.372000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17179622.372000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179622.372000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179622.372000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179622.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179622.380000] [fglrx] total      GART = 134217728
[17179622.380000] [fglrx] free       GART = 118222848
[17179622.380000] [fglrx] max single GART = 118222848
[17179622.384000] [fglrx] total      LFB  = 134217728
[17179622.384000] [fglrx] free       LFB  = 116387840
[17179622.384000] [fglrx] max single LFB  = 116387840
[17179622.384000] [fglrx] total      Inv  = 0
[17179622.384000] [fglrx] free       Inv  = 0
[17179622.384000] [fglrx] max single Inv  = 0
[17179622.384000] [fglrx] total      TIM  = 0
[17179622.856000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179622.856000] apm: overridden by ACPI.
[17179623.392000] ip_tables: (C) 2000-2002 Netfilter core team
[17179623.508000] Netfilter messages via NETLINK v0.30.
[17179623.568000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
[17179626.228000] Bluetooth: Core ver 2.8
[17179626.228000] NET: Registered protocol family 31
[17179626.228000] Bluetooth: HCI device and connection manager initialized
[17179626.228000] Bluetooth: HCI socket layer initialized
[17179626.328000] Bluetooth: L2CAP ver 2.8
[17179626.328000] Bluetooth: L2CAP socket layer initialized
[17179626.388000] Bluetooth: RFCOMM socket layer initialized
[17179626.388000] Bluetooth: RFCOMM TTY layer initialized
[17179626.388000] Bluetooth: RFCOMM ver 1.7
[17186983.228000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63298 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=59140 RES=0x00 ACK URGP=0
[17186997.992000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63892 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=65340 RES=0x00 ACK URGP=0
[17211189.460000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=222.212.170.145 DST=192.168.1.135 LEN=1454 TOS=0x00 PREC=0x00 TTL=108 ID=5354 DF PROTO=TCP SPT=6253 DPT=40152 WINDOW=64270 RES=0x00 ACK PSH URGP=0
[17231731.860000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=19558 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231736.868000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20028 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231746.836000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20881 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231764.552000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=22403 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK URGP=0
[17231766.900000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=22608 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK PSH URGP=0
[17231804.976000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=26000 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=65535 RES=0x00 ACK URGP=0
[17247631.392000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1)
[17247631.392000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xc8bfbae0 still mapped (user_handle = 0x00013000)
[17247631.400000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1), force it to be removed anyway
[17247631.408000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17306607.340000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17306608.304000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17306608.388000] NTFS volume version 3.1.
[17306844.692000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17306848.100000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17306848.100000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17306848.100000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17306848.100000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17306848.100000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17306848.100000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17306848.100000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17306848.112000] [fglrx] total      GART = 134217728
[17306848.112000] [fglrx] free       GART = 118222848
[17306848.112000] [fglrx] max single GART = 118222848
[17306848.112000] [fglrx] total      LFB  = 134217728
[17306848.112000] [fglrx] free       LFB  = 116387840
[17306848.112000] [fglrx] max single LFB  = 116387840
[17306848.112000] [fglrx] total      Inv  = 0
[17306848.112000] [fglrx] free       Inv  = 0
[17306848.112000] [fglrx] max single Inv  = 0
[17306848.112000] [fglrx] total      TIM  = 0
[17307254.904000] NTFS volume version 3.1.
hallvor@hallvor-desktop:~$

---

### Post by Hallvor on 2007-02-14
And this is the output of a shared NTFS-drive.

> hallvor@hallvor-desktop:~$ dmesg /dev/hdb5
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b50
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff79c0
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1830.220 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.216000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.216000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.228000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
[17179569.228000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.308000] Calibrating delay using timer specific routine.. 3664.14 BogoMIPS (lpj=7328298)
[17179569.308000] Security Framework v1.0.0 initialized
[17179569.308000] SELinux:  Disabled at boot.
[17179569.308000] Mount-cache hash table entries: 512
[17179569.308000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.308000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.308000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.308000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.308000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.308000] mtrr: v2.0 (20020519)
[17179569.308000] CPU: AMD Athlon(tm) XP 2500+ stepping 00
[17179569.308000] Enabling fast FPU save and restore... done.
[17179569.308000] Enabling unmasked SIMD FPU exception support... done.
[17179569.308000] Checking 'hlt' instruction... OK.
[17179569.324000] checking if image is initramfs... it is
[17179569.884000] Freeing initrd memory: 6617k freed
[17179569.900000] ACPI: Looking for DSDT ... not found!
[17179569.912000] ENABLING IO-APIC IRQs
[17179569.912000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.056000] NET: Registered protocol family 16
[17179570.056000] EISA bus registered
[17179570.056000] ACPI: bus type pci registered
[17179570.056000] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[17179570.056000] PCI: Using configuration type 1
[17179570.056000] ACPI: Subsystem revision 20051216
[17179570.060000] ACPI: Interpreter enabled
[17179570.060000] ACPI: Using IOAPIC for interrupt routing
[17179570.060000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.060000] PCI: Probing PCI hardware (bus 00)
[17179570.064000] PCI: nForce2 C1 Halt Disconnect fixup
[17179570.064000] Boot video device is 0000:02:00.0
[17179570.064000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179570.136000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.140000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.140000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179570.144000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179570.148000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179570.152000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.152000] pnp: PnP ACPI init
[17179570.160000] pnp: PnP ACPI: found 14 devices
[17179570.160000] PnPBIOS: Disabled by ACPI PNP
[17179570.160000] PCI: Using ACPI for IRQ routing
[17179570.160000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.200000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179570.200000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179570.200000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179570.200000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[17179570.200000] PCI: Bridge: 0000:00:08.0
[17179570.200000]   IO window: disabled.
[17179570.200000]   MEM window: ea000000-eaffffff
[17179570.200000]   PREFETCH window: disabled.
[17179570.200000] PCI: Bridge: 0000:00:1e.0
[17179570.200000]   IO window: c000-cfff
[17179570.200000]   MEM window: e8000000-e9ffffff
[17179570.200000]   PREFETCH window: c0000000-dfffffff
[17179570.200000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179570.200000] audit: initializing netlink socket (disabled)
[17179570.200000] audit(1171314349.200:1): initialized
[17179570.200000] VFS: Disk quotas dquot_6.5.1
[17179570.200000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.200000] Initializing Cryptographic API
[17179570.200000] io scheduler noop registered
[17179570.200000] io scheduler anticipatory registered
[17179570.200000] io scheduler deadline registered
[17179570.200000] io scheduler cfq registered
[17179570.200000] isapnp: Scanning for PnP cards...
[17179570.560000] isapnp: No Plug & Play device found
[17179570.572000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.576000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.576000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.576000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.576000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.576000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.580000] mice: PS/2 mouse device common for all mice
[17179570.580000] EISA: Probing bus 0 at eisa.0
[17179570.580000] Cannot allocate resource for EISA slot 4
[17179570.580000] Cannot allocate resource for EISA slot 5
[17179570.580000] EISA: Detected 0 cards.
[17179570.580000] NET: Registered protocol family 2
[17179570.612000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.620000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.620000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.620000] TCP: Hash tables configured (established 32768 bind 32768)
[17179570.620000] TCP reno registered
[17179570.620000] TCP bic registered
[17179570.620000] NET: Registered protocol family 1
[17179570.620000] NET: Registered protocol family 8
[17179570.620000] NET: Registered protocol family 20
[17179570.620000] Using IPI Shortcut mode
[17179570.620000] ACPI wakeup devices:
[17179570.620000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179570.620000] ACPI: (supports S0 S1 S4 S5)
[17179570.620000] Freeing unused kernel memory: 288k freed
[17179570.664000] vga16fb: initializing
[17179570.664000] vga16fb: mapped to 0xc00a0000
[17179570.800000] Console: switching to colour frame buffer device 80x25
[17179570.800000] fb0: VGA16 VGA frame buffer device
[17179571.816000] Capability LSM initialized
[17179571.980000] ACPI: Fan [FAN] (on)
[17179571.988000] ACPI: Thermal Zone [THRM] (51 C)
[17179572.432000] SCSI subsystem initialized
[17179572.436000] ACPI: bus type scsi registered
[17179572.436000] libata version 1.20 loaded.
[17179572.436000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179572.436000] NFORCE2: chipset revision 162
[17179572.436000] NFORCE2: not 100% native mode: will probe irqs later
[17179572.436000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179572.436000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179572.436000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179572.436000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.436000] Probing IDE interface ide0...
[17179572.952000] hdb: Maxtor 6Y120P0, ATA DISK drive
[17179573.008000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.008000] Probing IDE interface ide1...
[17179573.296000] hdc: IBM-DTTA-371010, ATA DISK drive
[17179573.744000] hdd: DVDRW 16X16, ATAPI CD/DVD-ROM drive
[17179573.800000] ide1 at 0x170-0x177,0x376 on irq 15
[17179573.828000] hdb: max request size: 128KiB
[17179573.836000] hdb: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(33)
[17179573.836000] hdb: cache flushes supported
[17179573.836000]  hdb: hdb1 hdb2 < hdb5 >
[17179573.856000] hdc: max request size: 128KiB
[17179573.860000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179573.860000] Uniform CD-ROM driver Revision: 3.20
[17179573.868000] hdc: 19746720 sectors (10110 MB) w/465KiB Cache, CHS=19590/16/63, UDMA(33)
[17179573.868000] hdc: cache flushes not supported
[17179573.868000]  hdc: hdc1 hdc2 < hdc5 >
[17179574.232000] usbcore: registered new driver usbfs
[17179574.232000] usbcore: registered new driver hub
[17179574.236000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179574.236000] **** SET: Misaligned resource pointer: de840c02 Type 07 Len 0
[17179574.236000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179574.236000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 177
[17179574.236000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179574.236000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179574.236000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179574.236000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xeb003000
[17179574.292000] hub 1-0:1.0: USB hub found
[17179574.292000] hub 1-0:1.0: 3 ports detected
[17179574.396000] **** SET: Misaligned resource pointer: de840902 Type 07 Len 0
[17179574.396000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179574.396000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 185
[17179574.396000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179574.396000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179574.396000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179574.396000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xeb004000
[17179574.452000] hub 2-0:1.0: USB hub found
[17179574.452000] hub 2-0:1.0: 3 ports detected
[17179574.556000] **** SET: Misaligned resource pointer: de840602 Type 07 Len 0
[17179574.556000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179574.556000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 193
[17179574.556000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179574.556000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179574.556000] ehci_hcd 0000:00:02.2: debug port 1
[17179574.556000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179574.556000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179574.556000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xeb005000
[17179574.556000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.556000] hub 3-0:1.0: USB hub found
[17179574.556000] hub 3-0:1.0: 6 ports detected
[17179574.744000] Attempting manual resume
[17179574.756000] kjournald starting.  Commit interval 5 seconds
[17179574.756000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.588000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.596000] agpgart: Detected NVIDIA nForce2 chipset
[17179590.604000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179590.964000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179590.964000] **** SET: Misaligned resource pointer: dfdc6622 Type 07 Len 0
[17179590.964000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179590.964000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 177
[17179590.964000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179591.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.304000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179591.304000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179591.476000] Floppy drive(s): fd0 is 1.44M
[17179591.484000] eth0: forcedeth.c: subsystem: 0147b:1c02 bound to 0000:00:04.0[17179591.484000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.496000] FDC 0 is a post-1991 82077
[17179591.524000] **** SET: Misaligned resource pointer: daf09aa2 Type 07 Len 0
[17179591.524000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[17179591.524000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 185
[17179591.524000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179591.548000] parport: PnPBIOS parport detected.
[17179591.548000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.656000] Real Time Clock Driver v1.12
[17179591.752000] input: PC Speaker as /class/input/input1
[17179591.844000] intel8x0_measure_ac97_clock: measured 52430 usecs
[17179591.844000] intel8x0: clocking to 47484
[17179592.020000] **** SET: Misaligned resource pointer: da8528c2 Type 07 Len 0
[17179592.020000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179592.020000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179592.020000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[17179592.264000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179592.292000] ts: Compaq touchscreen protocol output
[17179592.848000] lp0: using parport0 (interrupt-driven).
[17179593.040000] fuse init (API version 7.3)
[17179593.092000] Adding 441748k swap on /dev/hdc5.  Priority:-1 extents:1 across:441748k
[17179593.252000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179593.252000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 13 13 12 12  dBm Maximum
[17179593.288000] EXT3 FS on hdc1, internal journal
[17179593.484000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.484000] md: bitmap version 4.39
[17179594.268000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179594.464000] NET: Registered protocol family 17
[17179595.172000] cdrom: open failed.
[17179606.860000] ACPI: Power Button (FF) [PWRF]
[17179606.860000] ACPI: Power Button (CM) [PWRB]
[17179606.988000] ibm_acpi: ec object not found
[17179607.028000] pcc_acpi: loading...
[17179611.896000] eth0: no link during initialization.
[17179618.100000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179618.100000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179618.100000] [fglrx] module loaded - fglrx 8.33.6 [Jan  8 2007] on minor 0
[17179618.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179622.152000] ppdev: user-space parallel port driver
[17179622.372000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179622.372000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179622.372000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17179622.372000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179622.372000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179622.372000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179622.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179622.380000] [fglrx] total      GART = 134217728
[17179622.380000] [fglrx] free       GART = 118222848
[17179622.380000] [fglrx] max single GART = 118222848
[17179622.384000] [fglrx] total      LFB  = 134217728
[17179622.384000] [fglrx] free       LFB  = 116387840
[17179622.384000] [fglrx] max single LFB  = 116387840
[17179622.384000] [fglrx] total      Inv  = 0
[17179622.384000] [fglrx] free       Inv  = 0
[17179622.384000] [fglrx] max single Inv  = 0
[17179622.384000] [fglrx] total      TIM  = 0
[17179622.856000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179622.856000] apm: overridden by ACPI.
[17179623.392000] ip_tables: (C) 2000-2002 Netfilter core team
[17179623.508000] Netfilter messages via NETLINK v0.30.
[17179623.568000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
[17179626.228000] Bluetooth: Core ver 2.8
[17179626.228000] NET: Registered protocol family 31
[17179626.228000] Bluetooth: HCI device and connection manager initialized
[17179626.228000] Bluetooth: HCI socket layer initialized
[17179626.328000] Bluetooth: L2CAP ver 2.8
[17179626.328000] Bluetooth: L2CAP socket layer initialized
[17179626.388000] Bluetooth: RFCOMM socket layer initialized
[17179626.388000] Bluetooth: RFCOMM TTY layer initialized
[17179626.388000] Bluetooth: RFCOMM ver 1.7
[17186983.228000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63298 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=59140 RES=0x00 ACK URGP=0
[17186997.992000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=89.216.176.167 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=63892 DF PROTO=TCP SPT=57476 DPT=53007 WINDOW=65340 RES=0x00 ACK URGP=0
[17211189.460000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=222.212.170.145 DST=192.168.1.135 LEN=1454 TOS=0x00 PREC=0x00 TTL=108 ID=5354 DF PROTO=TCP SPT=6253 DPT=40152 WINDOW=64270 RES=0x00 ACK PSH URGP=0
[17231731.860000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=19558 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231736.868000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20028 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231746.836000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=20881 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=30955 RES=0x00 ACK PSH URGP=0
[17231764.552000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=22403 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK URGP=0
[17231766.900000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=86 TOS=0x00 PREC=0x00 TTL=109 ID=22608 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=49135 RES=0x00 ACK PSH URGP=0
[17231804.976000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=80.109.3.240 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=26000 DF PROTO=TCP SPT=5878 DPT=59695 WINDOW=65535 RES=0x00 ACK URGP=0
[17247631.392000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1)
[17247631.392000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xc8bfbae0 still mapped (user_handle = 0x00013000)
[17247631.400000] [fglrx:firegl_rmmap] *ERROR* map 0xc8bfbaf0 still in use (map_count=1), force it to be removed anyway
[17247631.408000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17306607.340000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17306608.304000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17306608.388000] NTFS volume version 3.1.
[17306844.692000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17306848.100000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17306848.100000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17306848.100000] [fglrx] AGP detected, AgpState   = 0x1f00421a (hardware caps of chipset)
[17306848.100000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17306848.100000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17306848.100000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17306848.100000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17306848.112000] [fglrx] total      GART = 134217728
[17306848.112000] [fglrx] free       GART = 118222848
[17306848.112000] [fglrx] max single GART = 118222848
[17306848.112000] [fglrx] total      LFB  = 134217728
[17306848.112000] [fglrx] free       LFB  = 116387840
[17306848.112000] [fglrx] max single LFB  = 116387840
[17306848.112000] [fglrx] total      Inv  = 0
[17306848.112000] [fglrx] free       Inv  = 0
[17306848.112000] [fglrx] max single Inv  = 0
[17306848.112000] [fglrx] total      TIM  = 0
[17307254.904000] NTFS volume version 3.1.
hallvor@hallvor-desktop:~$

It is a desktop computer, not a laptop. Amd 2500+ XP, 512 mb ram. Dual boot with Windows XP. Ubuntu is installed on a small 8 gb drive, and sharing a 100 gb NTFS-partition with Windows.

---

### Post by bettlebrox on 2007-02-14
> **dcstar said:**
> Personally, if I had a AMD CPU I would be using at least a 686 kernel, and preferably the K7 one.
I'd agree with that!

---

### Post by bettlebrox on 2007-02-14
> **Hallvor said:**
> And this is the output of a shared NTFS-drive.



It is a desktop computer, not a laptop. Amd 2500+ XP, 512 mb ram. Dual boot with Windows XP. Ubuntu is installed on a small 8 gb drive, and sharing a 100 gb NTFS-partition with Windows.
dmesg doesn't show what model the drive is ... any ideas? Maybe it's on the receipt, or what make and model is the system?

Looks like you forgot to the grep and gave the whole output of dmesg! ;)

---

### Post by Hallvor on 2007-02-15
Sorry about that. I`m a newbie. Here it is: 

> hallvor@hallvor-desktop:~$ dmesg |grep hdc
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179574.968000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd :DMA
[17179575.828000] hdc: IBM-DTTA-371010, ATA DISK drive
[17179576.392000] hdc: max request size: 128KiB
[17179576.396000] hdc: 19746720 sectors (10110 MB) w/465KiB Cache, CHS=19590/16/ 63, UDMA(33)
[17179576.396000] hdc: cache flushes not supported
[17179576.396000]  hdc: hdc1 hdc2 < hdc5 >
[17179595.672000] Adding 441748k swap on /dev/hdc5.  Priority:-1 extents:1 acros s:441748k
[17179595.856000] EXT3 FS on hdc1, internal journal
hallvor@hallvor-desktop:~$

---

### Post by bettlebrox on 2007-02-18
lshw should show all your hardware including the optical drive. 

Try:

sudo lshw | more

And see if you can ID the drive.

---

### Post by ZoRaC on 2007-02-20
Sorry, been offline a few days...

The problems occured even when I'm not connected to the internet, so that's not an issue.

My dmesg | grep hdb:
> [17179574.380000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[17179575.120000] hdb: TSSTcorpCD/DVDW SN-S082D, ATAPI CD/DVD-ROM drive
[17179575.400000] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179680.708000] hdb: status timeout: status=0xd0 { Busy }
[17179680.708000] hdb: DMA disabled
[17179680.756000] hdb: ATAPI reset complete

I got a Dell Inspiron 2200 laptop.

Someone suggested disableing DMA, but I've tried with it both enabled and disabled, no difference.

This is the part about hdb from lshw:
> *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorpCD/DVDW SN-S082D
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: SS03
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb

---

### Post by tschaboo on 2007-02-20
Since upgrading to edgy my system is also freezing for a few seconds in the following situations:
- when i'm getting a message through skype. but only if there's no chat window (with that contact) open yet or if the chat-window is already open but there was no conversation for a time ... probably >15 min.
- when accessing my encrypted partitions (kryptd is running nice -5)

i'm using an athlon xp 2000+ desktop processor with the -generic-kernel.

[edit]: i just noticed, that my skype-problem is a known issue: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53216)

---

### Post by bettlebrox on 2007-02-20
> **ZoRaC said:**
> Sorry, been offline a few days...

The problems occured even when I'm not connected to the internet, so that's not an issue.

My dmesg | grep hdb:


I got a Dell Inspiron 2200 laptop.

Someone suggested disableing DMA, but I've tried with it both enabled and disabled, no difference.

This is the part about hdb from lshw:
What kernel are you using? If either you or Hallivor are using a kernel less than 2.6.17 you should try upgrading to 2.6.17.

---

### Post by ZoRaC on 2007-02-21
From a few post back:
"2.6.17-11-generic, but I just upgraded from 2.6.17.10 two hours ago, but it didn't help."

I'm not running Skype, so that's not the cause in my case.

---

### Post by ZoRaC on 2007-02-21
I just tried re-flashing the firmware for my DVD-writer (it already had the newest version, SS03), but that didn't help either. :(

---

### Post by Hallvor on 2007-02-25
I have been using the latest kernel. It still freezes. (No problems in XP.)

---

### Post by bettlebrox on 2007-02-25
Then I guess it's time to submit a bug report.

---

### Post by Hallvor on 2007-03-07
Think I found the problem.. But I need just a little help. I suspected that the gnome network manager was the problem. The freezes and dropped connections seem to occur when the manager is searching for network connections. For some reason, it seems to do this about every 20 minutes. Anyway, I disabled all connections in the network manager, and the freezes were gone.

The bad part was that it left me without an internet connection, so I am writing this with the gnome network manager enabled.

I am connected to the internet through a wireless cnet-854 pci card, and I wonder: Is there a way to bypass the gnome network manager to connect to the internet? I tried  wifi-radar, but I could not make it work if I disabled the network manager. Don`t know is this is normal, but are there other options out there?


Hallvor

---

### Post by bettlebrox on 2007-03-07
Have a look at this:

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

You should be able to edit /etc/network/interfaces enable networking that way.

---

### Post by Hallvor on 2007-03-08
Thanks. I`ll try it later and let you know how it goes. Does that mean I can disable all connections through the network manager?

---

### Post by Hallvor on 2007-03-08
I think that was it. No freezes for 35 minutes, and I think they are gone for good. Let me tell you (and others with this problem) what I did: 

> sudo gedit /etc/network/interfaces

Then I edited the file: Originally, there were no "#" in the file, so I crossed out everything in the middle.

> auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid <MY ESSID>
wireless-key <MY KEY>

auto ra0

Save and exit!

Then restart: 

> sudo /etc/init.d/networking restart

That`s it!

This thread gave me the solution: [http://www.ubuntuforums.org/showthread.php?t=240770&highlight=ralink](http://www.ubuntuforums.org/showthread.php?t=240770&highlight=ralink)

Thanks to all of you!


Hallvor

---

### Post by ZoRaC on 2007-03-08
I just tried doing the same, but it didn't help at all... :(

My "interfaces":> auto lo
iface lo inet loopback


#iface eth0 inet dhcp


#iface eth1 inet dhcp
wireless-essid Epyon
wireless-key s:

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


#auto eth1

#auto eth

---

### Post by Hallvor on 2007-03-09
That was strange. Sorry it didn`t work out for you. Have you tested if the freezes come approximately every 20 minutes? Mine came excactly every 20 minutes.

You have saved your changes, restarted your network card, and made sure your wireless connection is the only one enabled in the network manager?



Hallvor

---

### Post by ZoRaC on 2007-03-09
The freezes are random... sometimes 5-6 times in a couple of mins, sometimes 1 time in 10 mins.

But, the syslog indicates something with hdb... So it probably isn't the same problem as you had.

---

### Post by Hallvor on 2007-03-09
Yes. Sounds like a different problem. You could always test with a different hard drive. It could be hardware related.

---

### Post by ZoRaC on 2007-03-09
"hdb" is my dvd-writer...
Got no others that I could use to test...

---

### Post by chinasteve2000 on 2007-05-30
To summarize what these posts have for we who are simple, I want to write down the advise I would give to an Ubuntu user using Skype:

There's a sound problem that is making your system freeze, and turning off one or two sounds can fix it. Open Skype, then click Tools / Options, and then click the Sounds button on the left.
Next, turn off 'connecting call' and/or 'contact online.' The first one is what freezes my computer, and the second is annoying. ;) 
Finally, try removing more for testing if you still freeze up. 

If you have multiple people using Skype user names on the same computer, or you have more than one Ubuntu user name, do the same for each user name.

Have fun Skyping!
-Steve
:popcorn:
(A big thanks to my friend Jim who first mentioned this solution to me)

---

### Post by Hallvor on 2007-05-31
I found out what caused the problems - it was not network related, though the problem seemed to occur less often after the fix above for some weird reason. The freezes were caused by the time synchronizing tool. It connected to a server on the internet to adjust the system time every 20 minutes. And when that happened, there would be a short hang that dropped connections in aMule and froze movies i watched for a couple of seconds. I disabled time synchronization, and everything works fine - except the system time, that is... :)

---

