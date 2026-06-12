---
title: "Cannot mount UDF DVD!!!! Please help!"
date: 2007-08-19
forum: General Help
---

### Post by kbzona on 2007-08-19
I dont know what to do... i tried everything, read dozens of threads but no one has came with the solution...

Here the error:

Cannot mount <<UDF Volume>>

mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f8b71fd-f0a0-4cfc-b6e4-50266626e99e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=77728140-ccd0-4529-93a5-87a66c7f6c89 /home           ext3    defaults        0       2
# /dev/sda2
UUID=d7f1fdf5-cd0b-4819-aa88-8d2179533143 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0


dmesg | tail
[ 8090.809128] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.182.30 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=61156 DF PROTO=TCP SPT=3209 DPT=445 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 8103.687644] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.160.154 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=46589 DF PROTO=TCP SPT=3138 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8106.703723] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.160.154 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=47525 DF PROTO=TCP SPT=3138 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8117.438975] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=222.191.251.93 DST=192.168.0.101 LEN=40 TOS=0x00 PREC=0x00 TTL=99 ID=256 PROTO=TCP SPT=6000 DPT=6588 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 8119.666034] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.50.194 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=62835 DF PROTO=TCP SPT=3838 DPT=2967 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8122.598601] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.50.194 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=63178 DF PROTO=TCP SPT=3838 DPT=2967 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8140.178969] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.131.125 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=2443 DF PROTO=TCP SPT=4801 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8143.132671] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.131.125 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=2826 DF PROTO=TCP SPT=4801 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8150.119068] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.161.18 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=6761 DF PROTO=TCP SPT=4939 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 8153.006440] Inbound IN=eth0 OUT= MAC=04:4b:80:80:80:03:00:13:46:4f:ee:73:08:00 SRC=190.45.161.18 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=7723 DF PROTO=TCP SPT=4939 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 


thxn in advance

---

### Post by BoneKracker on 2007-08-19
Your fstab looks fine.  The dmesg entries you posted have nothing to do with it (they're showing samba network traffic through your firewall or something).

A couple things that might provide clues:
What happens with the same udf disk in your other drive?
What happens with other udf disks (known to be good) in the same drive?
What happens when you switch the fstab entry from 'udf,iso9660' to 'auto'?

---

### Post by kbzona on 2007-08-19
1) my other drive is a CD-rom only :(

2) ive tried other UDF dvd's and they work fine....   and the DVD that gives problem can be readed in windows with no problems..

3) nothing happens... the same error... also tried iso9660,udf  but no go

---

### Post by kbzona on 2007-08-19
Ive noticed an interesting thing:

I can mount DVD-R  udf  but no DVD+R udf

---

### Post by BoneKracker on 2007-08-19
So it's disk-specific.

Read this, focusing on the section: "Why a computer might not read a particular UDF disk".
[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

---

### Post by kbzona on 2007-08-19
And does a workaround or fix exist for feisty??

---

### Post by chunbeke on 2007-08-19
ouhhh i have the same problem dude, 
i don't know how to fix it :(

---

### Post by kbzona on 2007-08-19
Well, this is getting really really weird....

I can open DVD+R and DVD-R.... but there are some DVD's that cant open but open fine in windows

---

### Post by BoneKracker on 2007-08-19
I don't know.  I've never had this problem.  My intuition tells me, though, that it might be the problem described in that wp article (assuming this is a home-baked disk).  I don't want to send you on a wild goose chase, though.

If it were me, and I really needed access to the disk, I would see if I could extract the contents from the dvd from within windows, and then burn a new dvd from within linux.

If that wouldn't work, I'd probably research how to determine the version of udf used on the dvd, how to determine if vat or spared flavor is in use, what versions of udf the kernel is supposed to handle, and whether there are known issues pertaining to the kernel udf driver and/or its support for udf versions and flavors.  Search the forums.  Google.  Search kernel trap.  Search newsgroups. The usual.

What have you got on there that's so important you would switch operating systems just so you can get to it -- your kiddie porn collection you had to personally butt-mule into country from Thailand or something? :)

---

### Post by kbzona on 2007-08-19
> What have you got on there that's so important you would switch operating systems just so you can get to it -- your kiddie porn collection you had to personally butt-mule into country from Thailand or something? 

Well certainly not... i have important documents, some apps, some music....


I hope to fix this with Gutsy arrival :)   ...  anyway just in case i installed gutsy kernel and the problem persist :(

I think is what u r saying about the UDF versions.. maybe this kernels doesnt have the latest version ???

---

### Post by BoneKracker on 2007-08-19
> Well certainly not... i have important documents, some apps, some music....Sorry - that was supposed to funny.  Yes, if it's stuff like that, it might be easiest just to re-burn it.  Copy the files to a mutually-accessible partition, boot into Linux, and full-erase/burn the disk (although you might want to change media too).
> I think is what u r saying about the UDF versions.. maybe this kernels doesnt have the latest version ???I'm only guessing; I have no reason to believe that.  But yes, that's sort of what I'm saying.  Not necessarily that it doesn't have the "latest" version *per se* -- just that it might not have a compatible implementation of one of those "standards" (version/flavor).  Certain large software companies have been known to deviate slightly from actual standards when it suits them.  So it's possible that the disk was burned with a utility that didn't implement the new version of udf in exactly the same way Linux has, or that the utility used one of those "flavors" and it isn't supported in the kernel, or that it used one of those "flavors" but implemented it in a way that's not compatible.  Or, yes, that the kernel doesn't support the "latest" version (but I doubt that's the case).

I repeat, though, that I am only guessing -- trying to offer what little direction my pea-sized brain can -- to help you possibly narrow down your search for the solution.  I am not familiar with the problem, and I'm not familiar with the details of Linux' udf implementation (or anybody elses).

---

### Post by kbzona on 2007-08-20
Now a weird thing is happening... K3b recognizes and read the folders of the DVD but im not able to manipulate files

---

### Post by kbzona on 2007-08-21
Bump

---

### Post by keyboardslave on 2007-08-26
im having the some troubles try changing from udf,iso9660 in fstab to auto.

that works for people... not me though :(

---

### Post by kbzona on 2007-08-26
Yes i tried that too, i tried EVERYTHING!!!... but wont work...
So i think that the problems is in the kernel itself . maybe its not implemented yet... who knows...


BTW I've installed VMWare with windows inside it and DVD works perfect....

---

### Post by Cubells on 2007-09-04
> **kbzona said:**
> Yes i tried that too, i tried EVERYTHING!!!... but wont work...
So i think that the problems is in the kernel itself . maybe its not implemented yet... who knows...


BTW I've installed VMWare with windows inside it and DVD works perfect....

Try adding ro option to the fstab line as you can see: udf,iso9660,ro

It works for me!

---

### Post by kbzona on 2007-09-04
udf,iso9660,ro
"Unknown filesystem 'ro'  "

BTW, ro should be in the options... how it works for you?? becaouse ro is not a filesystem AFAIK....

---

### Post by Cubells on 2007-09-04
> **kbzona said:**
> udf,iso9660,ro
"Unknown filesystem 'ro'  "

BTW, ro should be in the options... how it works for you?? becaouse ro is not a filesystem AFAIK....

Sorry, It's a mistake!!

'ro' must be in the options:

user,noauto,ro

Now, it's ok...

---

### Post by kbzona on 2007-09-05
as i said in 4 post down, i think is a problem with the kernel... missing things, things that are not implemented yet... I havent tried Gutsy... but i'll wait until his final release and hop e to fix this problem

---

### Post by Cubells on 2007-09-05
> **kbzona said:**
> as i said in 4 post down, i think is a problem with the kernel... missing things, things that are not implemented yet... I havent tried Gutsy... but i'll wait until his final release and hop e to fix this problem

I think it ins't a kernel bug.
You have not attached any message that aims to this possibility.

There is a very known bug for your problem: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233/](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233/)

Attila points out: "The bug is in "mount" and I've managed to fix it. It has nothing to do with UDF or ISO9660, and it's not Ubuntu-specific: "mount" may fail when you try to mount a read-only device in read/write mode and you specify more than one file system type. It works only if the correct file system type is the last one in the list."

This bug has a workaround until the patch was published: &#65279;Simply you have to substitute the filesystems udf,iso9660 for auto, and &#65279;It would have to work to you.

If it wouldn't, attach the output of the command "dmesg" and we try again...

Cheers,...

---

### Post by kbzona on 2007-09-05
I think that isnt my problem too... and as i said in my first post.. i almost tried everything...

anyways here is dmesg

btw this is the error:

mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error

```
dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1
.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-1
6.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 en
d: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 en
d: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 en
d: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fde0000 en
d: 000000003fee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fee0000 size: 0000000000003000 en
d: 000000003fee3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fee3000 size: 000000000000d000 en
d: 000000003fef0000 type: 3
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000010000 en
d: 000000003ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 en
d: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 en
d: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4200
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f
8150
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x
3fee3040
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x
3fee30c0
[    0.000000] ACPI: SRAT (v001 AMD    HAMMER   0x00000001 AMD  0x00000001) @ 0x
3fee92c0
[    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x
3fee93c0
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x
3fee9200
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x
00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a010
0000)
[    0.000000] Detected 2280.656 MHz processor.
[   16.371503] Built 1 zonelists.  Total pages: 259811
[   16.371505] Kernel command line: root=UUID=579662f2-fd1b-4e11-bc8a-b8b714e9de
85 ro quiet splash
[   16.371613] mapped APIC to ffffd000 (fee00000)
[   16.371615] mapped IOAPIC to ffffc000 (fec00000)
[   16.371617] Enabling fast FPU save and restore... done.
[   16.371619] Enabling unmasked SIMD FPU exception support... done.
[   16.371624] Initializing CPU#0
[   16.371654] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.371696] spurious 8259A interrupt: IRQ7.
[   16.372381] Console: colour VGA+ 80x25
[   16.372622] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.372906] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.387402] Memory: 1027244k/1047424k available (1993k kernel code, 19460k re
served, 900k data, 328k init, 129920k highmem)
[   16.387411] virtual kernel memory layout:
[   16.387412]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.387413]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.387414]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.387415]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.387416]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   16.387417]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   16.387418]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   16.387420] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   16.463457] Calibrating delay using timer specific routine.. 4564.04 BogoMIPS
 (lpj=9128093)
[   16.463486] Security Framework v1.0.0 initialized
[   16.463490] SELinux:  Disabled at boot.
[   16.463501] Mount-cache hash table entries: 512
[   16.463589] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 000
00000 00000001 00000000 00000001
[   16.463595] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.463597] CPU: L2 Cache: 512K (64 bytes/line)
[   16.463599] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 0
0000001 00000000 00000001
[   16.463607] Compat vDSO mapped to ffffe000.
[   16.463609] Remapping vsyscall page to ffffe000
[   16.463616] Checking 'hlt' instruction... OK.
[   16.479505] SMP alternatives: switching to UP code
[   16.479631] Freeing SMP alternatives: 11k freed
[   16.479765] Early unpacking initramfs... done
[   16.720103] ACPI: Core revision 20060707
[   16.722318] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found,
using machine DSDT.
[   16.726345] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[   16.726357] Total of 1 processors activated (4564.04 BogoMIPS).
[   16.726483] ENABLING IO-APIC IRQs
[   16.726654] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   16.870588] Brought up 1 CPUs
[   16.870736] Booting paravirtualized kernel on bare hardware
[   16.870779] Time: 12:32:51  Date: 08/05/107
[   16.870795] NET: Registered protocol family 16
[   16.870845] EISA bus registered
[   16.870848] ACPI: bus type pci registered
[   16.875082] PCI: PCI BIOS revision 3.00 entry at 0xfa610, last bus=5
[   16.875084] PCI: Using configuration type 1
[   16.875085] Setting up standard PCI resources
[   16.882437] ACPI: Interpreter enabled
[   16.882439] ACPI: Using IOAPIC for interrupt routing
[   16.882849] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.882852] PCI: Probing PCI hardware (bus 00)
[   16.885146] PCI: Transparent bridge - 0000:00:09.0
[   16.885322] Boot video device is 0000:05:00.0
[   16.885398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.942081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.943560] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.943816] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   16.944073] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   16.944329] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[   16.944585] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.944841] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   16.945097] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.945353] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.945610] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   16.945868] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.946124] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[   16.946383] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   16.946649] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.946913] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.947180] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   16.947446] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *
0, disabled.
[   16.947741] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   16.948030] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   16.948320] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   16.948609] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   16.948829] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   16.949130] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   16.949433] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   16.949734] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   16.950035] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   16.950335] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   16.950641] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   16.950941] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   16.951242] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   16.951551] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   16.951860] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   16.952169] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   16.953659] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.953669] pnp: PnP ACPI init
[   16.958389] pnp: PnP ACPI: found 11 devices
[   16.958392] PnPBIOS: Disabled by ACPI PNP
[   16.958421] PCI: Using ACPI for IRQ routing
[   16.958425] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[   17.010777] NET: Registered protocol family 8
[   17.010779] NET: Registered protocol family 20
[   17.011154] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   17.011157] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   17.011159] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   17.011161] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   17.011163] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   17.011165] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   17.011330] PCI: Bridge: 0000:00:09.0
[   17.011332]   IO window: a000-afff
[   17.011335]   MEM window: fde00000-fdefffff
[   17.011337]   PREFETCH window: fdf00000-fdffffff
[   17.011339] PCI: Bridge: 0000:00:0b.0
[   17.011341]   IO window: 9000-9fff
[   17.011343]   MEM window: fdd00000-fddfffff
[   17.011345]   PREFETCH window: fdc00000-fdcfffff
[   17.011347] PCI: Bridge: 0000:00:0c.0
[   17.011349]   IO window: 8000-8fff
[   17.011351]   MEM window: fdb00000-fdbfffff
[   17.011353]   PREFETCH window: fda00000-fdafffff
[   17.011355] PCI: Bridge: 0000:00:0d.0
[   17.011357]   IO window: 7000-7fff
[   17.011359]   MEM window: fd900000-fd9fffff
[   17.011361]   PREFETCH window: fd800000-fd8fffff
[   17.011364] PCI: Bridge: 0000:00:0e.0
[   17.011366]   IO window: 6000-6fff
[   17.011368]   MEM window: fd700000-fd7fffff
[   17.011370]   PREFETCH window: d0000000-dfffffff
[   17.011376] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   17.011382] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   17.011386] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.011391] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.011395] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   17.011412] NET: Registered protocol family 2
[   17.046225] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.046324] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[   17.046827] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.047067] TCP: Hash tables configured (established 131072 bind 65536)
[   17.047069] TCP reno registered
[   17.058239] checking if image is initramfs... it is
[   17.531069] Freeing initrd memory: 6768k freed
[   17.531327] audit: initializing netlink socket (disabled)
[   17.531336] audit(1188995572.244:1): initialized
[   17.531375] highmem bounce pool size: 64 pages
[   17.531413] VFS: Disk quotas dquot_6.5.1
[   17.531424] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.531455] io scheduler noop registered
[   17.531457] io scheduler anticipatory registered
[   17.531458] io scheduler deadline registered
[   17.531464] io scheduler cfq registered (default)
[   25.539440] 0000:00:02.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   25.539450] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   25.539457] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.539462] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   25.539469] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.539473] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   25.539480] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.539485] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   25.539491] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.539601] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   25.539621] assign_interrupt_mode Found MSI capability
[   25.539623] Allocate Port Service[0000:00:0b.0:pcie00]
[   25.539667] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   25.539684] assign_interrupt_mode Found MSI capability
[   25.539686] Allocate Port Service[0000:00:0c.0:pcie00]
[   25.539728] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   25.539746] assign_interrupt_mode Found MSI capability
[   25.539747] Allocate Port Service[0000:00:0d.0:pcie00]
[   25.539792] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.539808] assign_interrupt_mode Found MSI capability
[   25.539810] Allocate Port Service[0000:00:0e.0:pcie00]
[   25.539881] isapnp: Scanning for PnP cards...
[   25.891963] isapnp: No Plug & Play device found
[   25.906950] Real Time Clock Driver v1.12ac
[   25.906981] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[   25.907353] mice: PS/2 mouse device common for all mice
[   25.907661] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   25.907794] input: Macintosh mouse button emulation as /class/input/input0
[   25.907813] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.907816] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[   25.907926] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[   25.910955] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.910959] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.911037] EISA: Probing bus 0 at eisa.0
[   25.911041] Cannot allocate resource for EISA slot 1
[   25.911051] Cannot allocate resource for EISA slot 6
[   25.911052] Cannot allocate resource for EISA slot 7
[   25.911054] Cannot allocate resource for EISA slot 8
[   25.911055] EISA: Detected 0 cards.
[   25.941052] TCP cubic registered
[   25.941057] NET: Registered protocol family 1
[   25.941070] Using IPI No-Shortcut mode
[   25.941104] ACPI: (supports S0 S1 S3 S4 S5)
[   25.941140]   Magic number: 7:143:531
[   25.941360] Freeing unused kernel memory: 328k freed
[   25.942735] Time: tsc clocksource has been installed.
[   25.983398] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.128947] Capability LSM initialized
[   27.156426] ACPI: Fan [FAN] (on)
[   27.158977] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Dev
ice is not present [20060707]
[   27.159936] ACPI: Thermal Zone [THRM] (40 C)
[   27.541653] usbcore: registered new interface driver usbfs
[   27.541670] usbcore: registered new interface driver hub
[   27.541684] usbcore: registered new device driver usb
[   27.542145] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[   27.542471] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   27.542478] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (lev
el, low) -> IRQ 16
[   27.542487] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.542489] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   27.542570] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus numbe
r 1
[   27.542582] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[   27.583158] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.59.
[   27.621312] ieee1394: Initialized config rom entry `ip1394'
[   27.632903] usb usb1: configuration #1 chosen from 1 choice
[   27.632920] hub 1-0:1.0: USB hub found
[   27.632927] hub 1-0:1.0: 10 ports detected
[   27.739056] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   27.739063] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (lev
el, low) -> IRQ 17
[   27.739072] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   27.739074] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   27.739089] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus numbe
r 2
[   27.739109] ehci_hcd 0000:00:02.1: debug port 1
[   27.739112] PCI: cache line size of 64 is not supported by device 0000:00:02.
1
[   27.739119] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfeb00000
[   27.739124] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[   27.739168] usb usb2: configuration #1 chosen from 1 choice
[   27.739184] hub 2-0:1.0: USB hub found
[   27.739189] hub 2-0:1.0: 10 ports detected
[   27.846808] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   27.846821] NFORCE-CK804: chipset revision 162
[   27.846823] NFORCE-CK804: not 100% native mode: will probe irqs later
[   27.846828] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   27.846833]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DM
A
[   27.846840]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DM
A
[   27.846845] Probing IDE interface ide0...
[   28.584791] hda: GCR-8523B, ATAPI CD/DVD-ROM drive
[   28.696473] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   28.914011] usb 1-2: configuration #1 chosen from 1 choice
[   29.223311] usb 1-4: new full speed USB device using ohci_hcd and address 3
[   29.367063] hdb: HL-DT-ST DVDRAM GSA-H42N, ATAPI CD/DVD-ROM drive
[   29.425489] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.427865] usb 1-4: configuration #1 chosen from 1 choice
[   29.430031] Probing IDE interface ide1...
[   29.439939] usbcore: registered new interface driver hiddev
[   29.449834] input: HID 1241:1177 as /class/input/input2
[   29.449847] input: USB HID v1.00 Mouse [HID 1241:1177] on usb-0000:00:02.0-2
[   29.449857] usbcore: registered new interface driver usbhid
[   29.449859] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   30.001967] SCSI subsystem initialized
[   30.005469] libata version 2.20 loaded.
[   30.006580] sata_nv 0000:00:07.0: version 3.3
[   30.006974] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   30.006981] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (lev
el, low) -> IRQ 18
[   30.006989] sata_nv 0000:00:07.0: Using ADMA mode
[   30.006997] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   30.007044] ata1: SATA max UDMA/133 cmd 0xf884a480 ctl 0xf884a4a0 bmdma 0x000
1d400 irq 18
[   30.007075] ata2: SATA max UDMA/133 cmd 0xf884a580 ctl 0xf884a5a0 bmdma 0x000
1d408 irq 18
[   30.007082] scsi0 : sata_nv
[   30.320888] ata1: SATA link down (SStatus 0 SControl 300)
[   30.320896] scsi1 : sata_nv
[   30.632200] ata2: SATA link down (SStatus 0 SControl 300)
[   30.633081] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   30.633087] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (lev
el, low) -> IRQ 19
[   30.633094] sata_nv 0000:00:08.0: Using ADMA mode
[   30.633103] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   30.633142] ata3: SATA max UDMA/133 cmd 0xf884c480 ctl 0xf884c4a0 bmdma 0x000
1c000 irq 19
[   30.633171] ata4: SATA max UDMA/133 cmd 0xf884c580 ctl 0xf884c5a0 bmdma 0x000
1c008 irq 19
[   30.633179] scsi2 : sata_nv
[   31.103173] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.111312] ata3.00: ata_hpa_resize 1: sectors = 156312576, hpa_sectors = 156
312576
[   31.111315] ata3.00: ATA-6: WDC WD800JD-23JNA1, 06.01C06, max UDMA/133
[   31.111317] ata3.00: 156312576 sectors, multi 16: LBA
[   31.123280] ata3.00: ata_hpa_resize 1: sectors = 156312576, hpa_sectors = 156
312576
[   31.123283] ata3.00: configured for UDMA/133
[   31.123287] scsi3 : sata_nv
[   31.438420] ata4: SATA link down (SStatus 0 SControl 300)
[   31.438488] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ
: 0 ANSI: 5
[   31.438493] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFF
F, hw segs 61
[   31.443644] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   31.443648] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (lev
el, low) -> IRQ 16
[   31.443653] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.443659] forcedeth: using HIGHDMA
[   31.455996] hda: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[   31.456002] Uniform CD-ROM driver Revision: 3.20
[   31.461926] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDM
A(66)
[   31.462408] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[   31.462419] sda: Write Protect is off
[   31.462421] sda: Mode Sense: 00 3a 00 00
[   31.462430] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[   31.462464] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[   31.462469] sda: Write Protect is off
[   31.462471] sda: Mode Sense: 00 3a 00 00
[   31.462480] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[   31.462482]  sda: sda1 sda2 sda3
[   31.495977] sd 2:0:0:0: Attached scsi disk sda
[   31.498978] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   31.663464] Attempting manual resume
[   31.663467] swsusp: Resume From Partition 8:2
[   31.663468] PM: Checking swsusp image.
[   31.663581] PM: Resume from disk failed.
[   31.673464] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.673467] EXT3-fs: write access will be enabled during recovery.
[   31.965701] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:0a.0
[   31.966008] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   31.966015] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (lev
el, low) -> IRQ 20
[   32.018662] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fdefe000
-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.023903] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   32.023907] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (lev
el, low) -> IRQ 21
[   32.023932] skge 1.9 addr 0xfdef8000 irq 21 chip Yukon-Lite rev 9
[   32.023998] skge eth1: addr 00:01:29:d5:33:ec
[   33.298347] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200004d5b6]
[   33.328984] kjournald starting.  Commit interval 5 seconds
[   33.328994] EXT3-fs: recovery complete.
[   33.329219] EXT3-fs: mounted filesystem with ordered data mode.
[   39.366296] skge eth1: enabling interface
[   40.855507] NET: Registered protocol family 17
[   40.867356] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.868547] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.229163] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   41.229185] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   41.247193] Linux video capture interface: v2.00
[   41.448031] input: PC Speaker as /class/input/input3
[   41.508154] Linux agpgart interface v0.102 (c) Dave Jones
[   41.589341] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.589623] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   41.589630] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (lev
el, low) -> IRQ 22
[   41.589637] saa7133[0]: found at 0000:01:07.0, rev: 208, irq: 22, latency: 32
, mmio: 0xfdeff000
[   41.589641] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/11
0i (saa7133) [card=77,autodetected]
[   41.589649] saa7133[0]: board init: gpio is 200c000
[   41.591409] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev
3 if 0 alt 0 proto 2 vid 0x054C pid 0x01C7
[   41.591419] usbcore: registered new interface driver usblp
[   41.591421] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   41.686123] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies,
Starnberg, GERMANY' taints kernel.
[   41.688185] [fglrx] Maximum main memory to use for locked dma buffers: 928 MB
ytes.
[   41.688188] [fglrx] USWC is disabled in module parameters
[   41.688190] [fglrx] PAT is disabled!
[   41.688200] [fglrx] module loaded - fglrx 8.40.4 [Jul 31 2007] on minor 0
[   41.722074] input: Pinnacle PCTV as /class/input/input4
[   41.722098] ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0
]]
[   41.782206] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55
 d2 b2 92
[   41.782213] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff
 ff ff ff
[   41.782220] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 31 98 ff 00 a1 ff
 22 00 c2
[   41.782225] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 76 03
 1e 17 df
[   41.782231] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff
[   41.782237] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff
[   41.782243] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff
[   41.782249] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff
[   41.895142] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   41.951018] tuner 2-004b: setting tuner address to 61
[   42.002903] tuner 2-004b: type set to tda8290+75a
[   42.138603] tuner 2-004b: setting tuner address to 61
[   42.178515] tuner 2-004b: type set to tda8290+75a
[   42.260546] saa7133[0]: registered device video0 [v4l2]
[   42.260567] saa7133[0]: registered device vbi0
[   42.260585] saa7133[0]: registered device radio0
[   42.266557] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   42.266561] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (lev
el, low) -> IRQ 17
[   42.266577] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   42.275637] saa7134 ALSA driver for DMA sound loaded
[   42.275657] saa7133[0]/alsa: saa7133[0] at 0xfdeff000 irq 22 registered as ca
rd -2
[   42.589612] intel8x0_measure_ac97_clock: measured 58776 usecs
[   42.589614] intel8x0: clocking to 47021
[   42.714545] fuse init (API version 7.8)
[   42.761673] lp: driver loaded but no devices found
[   42.801114] Adding 979956k swap on /dev/disk/by-uuid/1da4d231-76a5-4577-967f-
a311b70587af.  Priority:-1 extents:1 across:979956k
[   42.898615] EXT3 FS on sda1, internal journal
[   43.408692] kjournald starting.  Commit interval 5 seconds
[   43.408846] EXT3 FS on sda3, internal journal
[   43.408850] EXT3-fs: mounted filesystem with ordered data mode.
[   43.942727] NET: Registered protocol family 10
[   43.942796] lo: Disabled Privacy Extensions
[   43.943088] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   47.213709] input: Power Button (FF) as /class/input/input5
[   47.216933] ACPI: Power Button (FF) [PWRF]
[   47.244481] input: Power Button (CM) as /class/input/input6
[   47.247690] ACPI: Power Button (CM) [PWRB]
[   47.279304] No dock devices found.
[   47.359914] ibm_acpi: ec object not found
[   47.386170] Using specific hotkey driver
[   47.414537] pcc_acpi: loading...
[   47.603597] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors
 (version 2.00.00)
[   47.608146] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   50.487549] ppdev: user-space parallel port driver
[   51.006143] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   51.006146] apm: overridden by ACPI.
[   51.461216] Bluetooth: Core ver 2.11
[   51.461446] NET: Registered protocol family 31
[   51.461447] Bluetooth: HCI device and connection manager initialized
[   51.461450] Bluetooth: HCI socket layer initialized
[   51.501040] Bluetooth: L2CAP ver 2.8
[   51.501043] Bluetooth: L2CAP socket layer initialized
[   51.503386] Bluetooth: RFCOMM socket layer initialized
[   51.503395] Bluetooth: RFCOMM TTY layer initialized
[   51.503396] Bluetooth: RFCOMM ver 1.8
[   52.411714] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (lev                                     el, low) -> IRQ 21
[   55.329616] [fglrx] total      GART = 130023424
[   55.329622] [fglrx] free       GART = 114032640
[   55.329624] [fglrx] max single GART = 114032640
[   55.329625] [fglrx] total      LFB  = 268304384
[   55.329627] [fglrx] free       LFB  = 250474496
[   55.329629] [fglrx] max single LFB  = 250474496
[   55.329630] [fglrx] total      Inv  = 0
[   55.329631] [fglrx] free       Inv  = 0
[   55.329633] [fglrx] max single Inv  = 0
[   55.329634] [fglrx] total      TIM  = 0
[   65.594765] eth0: no IPv6 routers present

```

---

### Post by protenniser on 2007-09-11
This UDF thing is a really funny problem for linux, but does anyone noticed this?
Take a DVD that is not mountable by linux, because of UDF, but mountable by winXP,
Open it in winXP and copy files to a mutual partition or open it in vmware and copy the files inside to your linux partition.
Burn all the files with K3B, it will warn you that because of the big files it switches to UDF file system and burn with UDF.
And the new DVD magically is recognized and mounted by linux. At least worked for me.
Does anybody else noticed?

---

### Post by baloo1974 on 2007-09-11
> **protenniser said:**
> This UDF thing is a really funny problem for linux, but does anyone noticed this?
Take a DVD that is not mountable by linux, because of UDF, but mountable by winXP,
Open it in winXP and copy files to a mutual partition or open it in vmware and copy the files inside to your linux partition.
Burn all the files with K3B, it will warn you that because of the big files it switches to UDF file system and burn with UDF.
And the new DVD magically is recognized and mounted by linux. At least worked for me.
Does anybody else noticed?

maybe but I have at least a hundred of DVD-s with a lot of my workmates on them ... so it will be verry hard to back up them and also creat a new library ... it is a tremenduos work, I still look for a simple, clare solution ... anyone??? thanks

---

### Post by protenniser on 2007-09-11
> **baloo1974 said:**
> maybe but I have at least a hundred of DVD-s with a lot of my workmates on them ... so it will be verry hard to back up them and also creat a new library ... it is a tremenduos work, I still look for a simple, clare solution ... anyone??? thanks

You are absolutely right. I am not saying this is a solution, it is only a backdoor for the files you should access immediately.

---

### Post by protenniser on 2007-09-13
I think I have solved the mount problem.
I have found it in the documentation of mount, worked for me, so I hope that it also works for you, please inform me about the object.
Let's say you have inserted a dvd (or something) that has udf file system on your cd(dvd) rom;
open a terminal and write;
```

sudo mount -t udf /dev/cdrom /media/cdrom

```
and hit enter, it may say that file system is write protected and mounting read-only, but it has worked for me!

---

### Post by kbzona on 2007-09-20
nope :( didnt work

---

### Post by shironeko on 2007-09-28
1- Install udftools

sudo aptitude install udftools

2- 

sudo mount -t udf /dev/cdrom /media/cdrom

---

### Post by cameran on 2007-10-01
having the exact same problem with commercial UDF discs (pc games) and none of the solutions work

anyone tried this on gutsy yet to see if DVDs "just work" ? (especially UDF ones)

cameran

---

### Post by kbzona on 2007-10-06
I  tried in Gutsy, but it doesnt works...

---

### Post by Circus-Killer on 2007-10-07
Having the same problem as the OP, tried everything suggested in this thread and others.
anyone know of a solution?

edit: its more worrying because the problem still exists in gutsy beta

---

### Post by Circus-Killer on 2007-10-08
is there absolutely no solution to this problem?

---

### Post by martinx73 on 2007-10-11
Hi 

i have 01 dvd rom in my machine.
i do not have more dvd rom or cd rom in my pc.
i need read 01 udf dvd.
in Xp this dvd work fine, but no work in ubuntu 7.04.
my solution is

to mount dvd only read
```
sudo mount -t udf /dev/cdrom /media/cdrom
```

to unmount
```
sudo umount -t udf /dev/cdrom /media/cdrom
```

regards

sorry my english is very basic

---

### Post by kbzona on 2007-11-28
nothing yet...  i hope this to be fixed in hardy :S

---

### Post by nae5 on 2007-11-28
I made this post 

[http://ubuntuforums.org/showthread.php?p=3800347#post3800347](http://ubuntuforums.org/showthread.php?p=3800347#post3800347)

a little while ago, there are a couple of related links in that post and i will add some more related links here:

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233/](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233/)
[http://ubuntuforums.org/showthread.php?t=591762&highlight=UDF](http://ubuntuforums.org/showthread.php?t=591762&highlight=UDF)
[http://www.uluga.ubuntuforums.org/showthread.php?t=510748&page=3](http://www.uluga.ubuntuforums.org/showthread.php?t=510748&page=3)

This seems to be a problem for many people.  A little more specifically changing udf,iso9660 to auto and installing udftools does not work for a lot of people.

Seems there are a few different types of UDF.  The wikipedia link earlier in this post is informative, but i still don't know how to solve this problem.  im not a coder, and for the most part am only capable of following/understanding solutions, not figuring them out myself, despite what getting into ubuntu has done for my computer knowledge.

Ubuntu rules.  But this is.. unacceptable isn't the right word, this will not stop me from ubuntuness, but I think that this is a big problem.  

While most of the other problems ive had with ubuntu i have been able to fix them, such as broadcom wireless card on my laptop,
this is a big deal since UDF seems to be the main "universal disc format" , no? especially for backing data up for those who don't yet have external hds or large flash sticks.

If Ubuntu wishes to make itself a more userfriendly, widely accepted OS, which i also want for ubuntu as well :O)  it seems that this problem should be decently high on the list, but every thread ive read on this problem has many people saying that editing fstab to auto or adding the ro option doesn't work, which is my case.  udftools didn't help anything either.

I think maybe this should be made into a serious effort to increase ubuntus compatibility, as i said before, for those who do not have external hds, or 4g flash sticks, or need to take data to another computer udf dvds are the best bet

When i first started with ubuntu i asked if i could bring my files with me. i was answered yes, and for the most part i could but there are still major holes...

---

### Post by Irihapeti on 2007-11-28
> **nae5 said:**
> 

I think maybe this should be made into a serious effort to increase ubuntus compatibility, as i said before, for those who do not have external hds, or 4g flash sticks, or need to take data to another computer udf dvds are the best bet


I agree. I'm in the situation you describe. A few DVDs are a LOT cheaper than external HDs or USB sticks where I live.

I did get writing to UDF to work, but it is so infernally SLOW that it's unusable - over 7 hours to write 2 GB.

---

### Post by thewarlock on 2007-12-08
none of the suggestions work for me (although it did in 7.04)

dmesg|tail..

[ 7065.321972] UDF-fs: Partition marked readonly; forcing readonly mount
[ 7065.423644] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2004/06/09 19:01 (1ed4)
[ 7564.308936] UDF-fs: Partition marked readonly; forcing readonly mount
[ 7564.377225] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2004/06/09 19:01 (1ed4)
[ 7667.907940] UDF-fs: Partition marked readonly; forcing readonly mount
[ 7667.970966] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2004/06/09 19:01 (1ed4)
[ 8095.740999] UDF-fs: Partition marked readonly; forcing readonly mount
[ 8095.843170] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO_RECORDER', timestamp 2004/06/09 19:01 (1ed4)

---

### Post by thewarlock on 2007-12-12
Ok, this is absolutely a bug in 7.10

I just tried a dvd that worked just fine in 7.04 and it fails in 7.10 on 3 different machines.
Gives the same dmesg info as my previous post.

So it is NOT the hardware, and it is NOT the dvds.  Something changed from feisty to gutsy that broke this.

The question is, what?

---

### Post by thewarlock on 2007-12-13
ok, changing the fstab to this fixed the problem.

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto     0       0


the bug forum had that suggestion, and it does work

seems the issue is that udf honors the file permissions, even if they are totally screwy.

---

### Post by bacdj on 2008-01-13
Firstly I have to say that I am not very competent with the technical side of computers alathough I have been using them for many years.

I am having difficulty with copying files from my C: HDD to my D: DVD burner.  I have always copied my important personal backup files onto a CD or DVD-RW disk for storage off site in case of theft or fire etc. and not had any trouble but in the past few months this has not been possible because the system shuts down part way through the transfer of files.

This is an error message I copied from one of the crashes if that means anything:
BCCode : 44 BCP1 : 83508DE0 BCP2 : 00000D63 BCP3 : 00000000 
BCP4 : 00000000 OSVer : 5_1_2600 SP : 2_0 Product : 768_1 

On some occasions I also got a message saying: 
“In the process of copying files the system stops and gives a message which says " The disk has been marked “read only” by UDF V2.00 writing software". On checking the disk it then shows to be full and will not allow any further adding to that disk.”

I have reformatted the CD’s and DVD’s with InCD, but the same problem reoccurs. 

I can use D drive for other functions (eg. Playing/copying CD’s/DVD’s etc) with no problems.

On searching the web for UDF V2.00 I was led to this site and noticed that some of the threads are very similar to mine although I use MS XP operating system.

Any assistance would be greatly appreciated, including how to change a CD/DVD-RW from being read only to writeable.

Brian DJ

---

### Post by byinbyan on 2008-01-14
Yeah...  I have had this exact same problem for months... Still haven't figured it out.  I can mount SOME UDF disks but others no.  I get that same error message.  I will examine the "flavor" of the disks... Maybe there is a workaround possible.  I'm thinking it may be a problem with UDF disks made with Vista.  UDFs that do mount are older disks.  Not yet certain of that but I do suspect it.

---

### Post by sadohert on 2008-05-07
> **thewarlock said:**
> ok, changing the fstab to this fixed the problem.

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto     0       0


the bug forum had that suggestion, and it does work

seems the issue is that udf honors the file permissions, even if they are totally screwy.

This did the trick exactly for me.  The problem in my /etc/fstab seemed to be that udf was listed before iso9660....so I changed my dvd rw fstab entry from:
```
/dev/scd0       /media/dvdrw   udf, iso9660 user,noauto,exec 0       0
```

TO:
```
/dev/scd0       /media/dvdrw   iso9660,udf user,noauto,exec 0       0
```

That's strange.  Order here made the difference (I tried auto at one point and that didn't work).

So, just to round out my post in case someone comes with similar issues, my problem came up when I was trying to access the files on a DVDR disc.  It was a Video DVD authored on an unknown system.  If I tried to list the contents of the video_ts folder the permissions and owner and group were all just a bunch of questions marks.  When mounting I woudl get the same issue where dmesg reported the disc being mounted readonly.  I could use totem to view the movie.  What I wanted to do was use Handbrake to rip the video files to divx, but as a normal user I could not view the contents of that video_ts folder.  Thankfully I could continue on my way by doing a "sudo" before the Handbrake command.  

Now, everythign seems to be fine and as a normal user I can now list the contents of that DVDR disc.

Thanks.
:guitar:

---

