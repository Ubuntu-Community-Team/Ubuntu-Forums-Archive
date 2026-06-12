---
title: "Can't mount USB drive from GUI, works fine via CLI"
date: 2008-04-27
forum: General Help
---

### Post by Daniel15 on 2008-04-27
Hi everyone, 
 I upgraded to Ubuntu 8.04, and it doesn't seem to be able to mount my USB drive (specifically, an MP3 player) via the CLI. If I go to Places -> Computer and double-click "USB Drive", I get:
> 
Unable to mount location

Can't mount file

However, running ```
sudo mount /dev/sdb1 /media/sdb1
``` in a terminal works fine.

Any ideas how to fix this?

---

### Post by ghost_ryder35 on 2008-04-27
since you have to use 'sudo' to mount it, ts probally because the volume is not in your fstab. try editing your fstab to make it work?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by danwood76 on 2008-04-27
Hal should auto mount the USB drive when its inserted.
You cant mount without root permissions thats why it works from the cli using sudo.

Have you added this drive to the fstab?

If you unplug the drive and plug it in does it automount?

---

### Post by Daniel15 on 2008-04-27
> can you edit your fstab to make it work?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
I shouldn't have to edit my fstab to get a USB storage device to mount, should I?

> Have you added this drive to the fstab?
Nope... But I didn't have to do that in Ubuntu 7.10?

> If you unplug the drive and plug it in does it automount?
Some output appears in /var/log/dmesg (showing that it's been detected), but it doesn't mount.

---

### Post by danwood76 on 2008-04-27
No I wouldnt add it to the fstab as it wont automount when inserted.

My automount is working fine.
Can you post the exact dmesg output after your insert?

---

### Post by Daniel15 on 2008-04-27
> [ 3875.085893] usb 1-3: USB disconnect, address 4
[ 3905.708980] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 3903.774866] usb 1-3: configuration #1 chosen from 1 choice
[ 3903.775450] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3903.775949] usb-storage: device found at 5
[ 3903.775957] usb-storage: waiting for device to settle before scanning
[ 3908.772601] usb-storage: device scan complete
[ 3910.840348] scsi 4:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[ 3909.785417] ready
[ 3909.786048] sd 4:0:0:0: [sdb] 1875968 2048-byte hardware sectors (3842 MB)
[ 3909.890055] sd 4:0:0:0: [sdb] Write Protect is off
[ 3909.890062] sd 4:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[ 3909.890065] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3911.958749] sd 4:0:0:0: [sdb] 1875968 2048-byte hardware sectors (3842 MB)
[ 3911.959750] sd 4:0:0:0: [sdb] Write Protect is off
[ 3911.959761] sd 4:0:0:0: [sdb] Mode Sense: 00 2a 00 00
[ 3911.959768] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3911.959776]  sdb: sdb1
[ 3911.962659]  sdb: p1 exceeds device capacity
[ 3911.963210] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 3911.963295] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3912.040061] attempt to access beyond end of device
[ 3912.040072] sdb: rw=0, want=4294967044, limit=7503872
[ 3912.040076] Buffer I/O error on device sdb1, logical block 1073741760
[ 3912.040081] attempt to access beyond end of device
[ 3912.040084] sdb: rw=0, want=4294967048, limit=7503872
[ 3912.040086] Buffer I/O error on device sdb1, logical block 1073741761
[ 3912.040090] attempt to access beyond end of device
[ 3912.040092] sdb: rw=0, want=4294967044, limit=7503872
[ 3912.040095] Buffer I/O error on device sdb1, logical block 1073741760
[ 3912.040098] attempt to access beyond end of device
[ 3912.040102] sdb: rw=0, want=4294967048, limit=7503872
[ 3912.040105] Buffer I/O error on device sdb1, logical block 1073741761
[ 3912.040117] attempt to access beyond end of device
[ 3912.040121] sdb: rw=0, want=4294967276, limit=7503872
[ 3912.040124] Buffer I/O error on device sdb1, logical block 1073741818
[ 3912.040128] attempt to access beyond end of device
[ 3912.040131] sdb: rw=0, want=4294967280, limit=7503872
[ 3912.040134] Buffer I/O error on device sdb1, logical block 1073741819
[ 3912.040139] attempt to access beyond end of device
[ 3912.040143] sdb: rw=0, want=4294967276, limit=7503872
[ 3912.040146] Buffer I/O error on device sdb1, logical block 1073741818
[ 3912.040149] attempt to access beyond end of device
[ 3912.040153] sdb: rw=0, want=4294967280, limit=7503872
[ 3912.040156] Buffer I/O error on device sdb1, logical block 1073741819
[ 3912.040221] attempt to access beyond end of device
[ 3912.040226] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040229] Buffer I/O error on device sdb1, logical block 1073741822
[ 3912.040234] attempt to access beyond end of device
[ 3912.040238] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040241] Buffer I/O error on device sdb1, logical block 1073741822
[ 3912.040250] attempt to access beyond end of device
[ 3912.040254] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040261] attempt to access beyond end of device
[ 3912.040265] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040271] attempt to access beyond end of device
[ 3912.040275] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040282] attempt to access beyond end of device
[ 3912.040285] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040292] attempt to access beyond end of device
[ 3912.040295] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040305] attempt to access beyond end of device
[ 3912.040308] sdb: rw=0, want=4294967228, limit=7503872
[ 3912.040312] attempt to access beyond end of device
[ 3912.040315] sdb: rw=0, want=4294967232, limit=7503872
[ 3912.040324] attempt to access beyond end of device
[ 3912.040327] sdb: rw=0, want=4294967284, limit=7503872
[ 3912.040331] attempt to access beyond end of device
[ 3912.040334] sdb: rw=0, want=4294967288, limit=7503872
[ 3912.040341] attempt to access beyond end of device
[ 3912.040345] sdb: rw=0, want=4294967292, limit=7503872
[ 3912.040352] attempt to access beyond end of device
[ 3912.040356] sdb: rw=0, want=4294967292, limit=7503872


Interesting, it seems to be trying to read beyond the end of the device for some reason O_o

I'm not sure if the same errors came up on Ubuntu 7.10, I never needed to fix anything, it "just worked".

---

### Post by ghost_ryder35 on 2008-04-27
have you ever used it with a windows machine and improperly dismounted it?  sometimes it will complain about things like that.  However I would try adding it to your fstab, more than likley will fix it.

---

### Post by Daniel15 on 2008-04-27
Never used it on a Windows machine.

I added it to my fstab:
> daniel@daniel-laptop:/media$ ls -la /dev/disk/by-label/
total 0
drwxr-xr-x 2 root root  60 2008-04-27 22:56 .
drwxr-xr-x 6 root root 120 2008-04-27 22:56 ..
lrwxrwxrwx 1 root root  10 2008-04-27 22:56 WALKMAN -> ../../sdb1

daniel@daniel-laptop:/media$ tail -n1 /etc/fstab
LABEL=WALKMAN /media/WALKMAN vfat noauto,user,rw


it still doesn't automatically mount, but I can now mount it using **mount /media/WALKMAN** at the command line. Still better I guess, but not as good as having it automatically mount (how it worked in Ubuntu 7.10) :(

---

### Post by ghost_ryder35 on 2008-04-27
did you do an 'upgrade' to hardy or a upgrade as in a fresh install?  if it was an 'upgrade' its probally just a clitch somewhere hate to say it

---

### Post by Daniel15 on 2008-04-27
This is a fresh install. I initially did an upgrade, but I was encountering so many problems (couldn't access anything in System -> Administration because it kept saying I didn't have permission, and other things mysteriously falling apart) that I thought it would be best to format and reinstall.

---

### Post by ghost_ryder35 on 2008-04-27
hmmm.... Funny that it doesnt work then.  you could write a little script to automount it everytime (you would just have to double click then !!!)

---

### Post by razta on 2008-04-27
Im having the same problem with all my USB storage devices. Can mount via CLI using:

```
$ sudo mount /dev/sdb1 /mnt/USB
```

But it does not auto detect the USB drives and add the icon to the desktop when I plug it in. I know I could just run the mount command every time I wanted to use it but my girlfriend also uses this PC and hasn't a clue about the CLI.

Heres my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c4e6bf9b-7632-4dba-bc8c-572c950e372e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9d45d72a-a389-48c1-bfb4-3155b4145360 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0
/dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0
```

It autodetected in 7.10 but since I upgraded to 8.04, it doesnt seem to work.

Any ideas?

---

### Post by ghost_ryder35 on 2008-04-27
> **razta said:**
> Im having the same problem with all my USB storage devices. Can mount via CLI using:
 
```
$ sudo mount /dev/sdb1 /usr/USB
```
 
But it does not auto detect the USB drives and add the icon to the desktop when I plug it in. I know I could just run the mount command every time I wanted to use it but my girlfriend also uses this PC and hasn't a clue about the CLI.
 
Heres my fstab:
 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c4e6bf9b-7632-4dba-bc8c-572c950e372e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9d45d72a-a389-48c1-bfb4-3155b4145360 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0
/dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0
```
 
It autodetected in 7.10 but since I upgraded to 8.04, it doesnt seem to work.
 
Any ideas?
your user permissions could be messed up.  you can check them out via the gui, make sure it allows you to mount devices

---

### Post by razta on 2008-04-27
Cant mount via GUI, ive been in "Users and Groups" and "Access external storage devices" is ticked. 

Should I start another thread? Feel as tho ive hijacked this one. :confused:

---

### Post by Daniel15 on 2008-04-27
> Should I start another thread? Feel as tho ive hijacked this one. 
I think your posts are fine here in this topic; our issues seem to basically be the same :)

> Cant mount via GUI, ive been in "Users and Groups" and "Access external storage devices" is ticked.
Same with me, it's ticked for me too.

---

### Post by danwood76 on 2008-04-27
Adding USB disks to the fstab stops hal from automounting it.
Unless the disk is attatched when you boot up.

It looks like, from your demsg output, that your USB disk is incorrectly partitioned, and the hal is trying to access data past the end of the disk.

What you could do is mount it manually then copy all the data off it (as its only 4GB right?) and reformat and repartition the USB drive.
Then try re plugging it.

---

### Post by razta on 2008-04-27
> **danwood76 said:**
> Adding USB disks to the fstab stops hal from automounting it.
Unless the disk is attatched when you boot up.

It looks like, from your demsg output, that your USB disk is incorrectly partitioned, and the hal is trying to access data past the end of the disk.

What you could do is mount it manually then copy all the data off it (as its only 4GB right?) and reformat and repartition the USB drive.
Then try re plugging it.

I have the same issue with all USB storage devices ive tried.

---

### Post by danwood76 on 2008-04-27
Do you get the same dmesg output?
(in terminal just type dmesg and it will dump it to you)

---

### Post by razta on 2008-04-27
```
ryan@ryan-desktop:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA340 checksum 0
[    0.000000] ACPI: RSDP 000FA340, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 0028 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 1FFF0030, 0074 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 1FFF0100, 3332 (r1    SiS      735      100 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=c4e6bf9b-7632-4dba-bc8c-572c950e372e ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1394.120 MHz processor.
[   31.631276] Console: colour VGA+ 80x25
[   31.631281] console [tty0] enabled
[   31.631930] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.632456] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.657508] Memory: 507556k/524224k available (2157k kernel code, 16036k reserved, 998k data, 364k init, 0k highmem)
[   31.657520] virtual kernel memory layout:
[   31.657521]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   31.657523]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.657525]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   31.657527]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   31.657528]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   31.657530]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   31.657532]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   31.657537] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.657603] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   31.737572] Calibrating delay using timer specific routine.. 2789.78 BogoMIPS (lpj=5579571)
[   31.737622] Security Framework initialized
[   31.737634] SELinux:  Disabled at boot.
[   31.737666] AppArmor: AppArmor initialized
[   31.737673] Failure registering capabilities with primary security module.
[   31.737688] Mount-cache hash table entries: 512
[   31.737902] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   31.737917] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.737921] CPU: L2 Cache: 256K (64 bytes/line)
[   31.737925] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   31.737942] Compat vDSO mapped to ffffe000.
[   31.737962] Checking 'hlt' instruction... OK.
[   31.753909] SMP alternatives: switching to UP code
[   31.755540] Freeing SMP alternatives: 11k freed
[   31.755758] Early unpacking initramfs... done
[   32.249956] ACPI: Core revision 20070126
[   32.250101] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.251916] ACPI: setting ELCR to 0200 (from 0820)
[   32.310005] CPU0: AMD Athlon(tm) XP 1600+ stepping 02
[   32.310014] SMP motherboard not detected.
[   32.310018] Local APIC not detected. Using dummy APIC emulation.
[   32.310111] Brought up 1 CPUs
[   32.310154] CPU0 attaching sched-domain:
[   32.310158]  domain 0: span 01
[   32.310161]   groups: 01
[   32.310528] net_namespace: 64 bytes
[   32.310543] Booting paravirtualized kernel on bare hardware
[   32.311246] Time: 19:46:48  Date: 04/27/08
[   32.311306] NET: Registered protocol family 16
[   32.311660] EISA bus registered
[   32.311678] ACPI: bus type pci registered
[   32.313126] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   32.313130] PCI: Using configuration type 1
[   32.313132] Setting up standard PCI resources
[   32.315666] ACPI: EC: Look up EC in DSDT
[   32.320049] ACPI: Interpreter enabled
[   32.320055] ACPI: (supports S0 S1 S4 S5)
[   32.320073] ACPI: Using PIC for interrupt routing
[   32.326477] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.326684] Enabling SiS 96x SMBus.
[   32.327183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.328846] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[   32.328983] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[   32.329104] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   32.329329] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[   32.329450] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   32.329569] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   32.329688] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   32.329806] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[   32.330118] ACPI: Power Resource [URP1] (off)
[   32.330155] ACPI: Power Resource [URP2] (off)
[   32.330190] ACPI: Power Resource [FDDP] (off)
[   32.330225] ACPI: Power Resource [LPTP] (off)
[   32.330299] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.330351] pnp: PnP ACPI init
[   32.330364] ACPI: bus type pnp registered
[   32.334805] pnp: PnP ACPI: found 13 devices
[   32.334809] ACPI: ACPI bus type pnp unregistered
[   32.334817] PnPBIOS: Disabled by ACPI PNP
[   32.335228] PCI: Using ACPI for IRQ routing
[   32.335234] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.349189] NET: Registered protocol family 8
[   32.349192] NET: Registered protocol family 20
[   32.349336] AppArmor: AppArmor Filesystem Enabled
[   32.353156] Time: tsc clocksource has been installed.
[   32.391887] PCI: Bridge: 0000:00:01.0
[   32.391890]   IO window: disabled.
[   32.391897]   MEM window: cda00000-cfafffff
[   32.391902]   PREFETCH window: bd800000-cd8fffff
[   32.391935] NET: Registered protocol family 2
[   32.429267] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   32.429644] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   32.430003] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   32.430372] TCP: Hash tables configured (established 16384 bind 16384)
[   32.430377] TCP reno registered
[   32.441362] checking if image is initramfs... it is
[   32.892828] Switched to high resolution mode on CPU 0
[   33.368716] Freeing initrd memory: 7425k freed
[   33.369804] audit: initializing netlink socket (disabled)
[   33.369832] audit(1209325608.660:1): initialized
[   33.373034] VFS: Disk quotas dquot_6.5.1
[   33.373166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.373409] io scheduler noop registered
[   33.373413] io scheduler anticipatory registered
[   33.373417] io scheduler deadline registered
[   33.373432] io scheduler cfq registered (default)
[   33.373486] PCI: Firmware left 0000:00:0b.0 e100 interrupts enabled, disabling
[   33.373497] Boot video device is 0000:01:00.0
[   33.373947] isapnp: Scanning for PnP cards...
[   33.727147] isapnp: No Plug & Play device found
[   33.772934] Real Time Clock Driver v1.12ac
[   33.773102] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.773285] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.773475] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.774403] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.774921] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.776264] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.776377] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.776545] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   33.776878] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.776886] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.788280] mice: PS/2 mouse device common for all mice
[   33.788483] EISA: Probing bus 0 at eisa.0
[   33.788525] EISA: Detected 0 cards.
[   33.788531] cpuidle: using governor ladder
[   33.788534] cpuidle: using governor menu
[   33.788783] NET: Registered protocol family 1
[   33.788831] Using IPI No-Shortcut mode
[   33.788893] registered taskstats version 1
[   33.789027]   Magic number: 4:269:800
[   33.789246]   hash matches device ptyr8
[   33.789331] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.789335] EDD information not available.
[   33.790134] Freeing unused kernel memory: 364k freed
[   33.816116] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   35.157246] fuse init (API version 7.9)
[   36.191027] usbcore: registered new interface driver usbfs
[   36.191071] usbcore: registered new interface driver hub
[   36.203066] usbcore: registered new device driver usb
[   36.218656] SCSI subsystem initialized
[   36.313154] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   36.313163] e100: Copyright(c) 1999-2006 Intel Corporation
[   36.313533] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   36.313538] PCI: setting IRQ 11 as level-triggered
[   36.313542] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   36.336213] e100: eth0: e100_probe: addr 0xcfffc000, irq 11, MAC addr 00:90:27:65:ad:de
[   36.338742] libata version 3.00 loaded.
[   36.350081] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.350468] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   36.350474] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   36.350501] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   36.350984] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   36.351017] ohci_hcd 0000:00:02.2: irq 11, io mem 0xcfffe000
[   36.408395] usb usb1: configuration #1 chosen from 1 choice
[   36.408440] hub 1-0:1.0: USB hub found
[   36.408456] hub 1-0:1.0: 3 ports detected
[   36.452790] Floppy drive(s): fd0 is 1.44M
[   36.473821] FDC 0 is a post-1991 82077
[   36.510520] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   36.510528] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   36.510554] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   36.510605] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   36.510628] ohci_hcd 0000:00:02.3: irq 11, io mem 0xcffff000
[   36.568246] usb usb2: configuration #1 chosen from 1 choice
[   36.568291] hub 2-0:1.0: USB hub found
[   36.568306] hub 2-0:1.0: 3 ports detected
[   36.683591] pata_sis 0000:00:02.5: version 0.5.2
[   36.686100] scsi0 : pata_sis
[   36.687748] scsi1 : pata_sis
[   36.688717] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   36.688723] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   36.813892] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   36.850340] ata1.00: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[   36.850349] ata1.00: 80293248 sectors, multi 16: LBA 
[   36.866121] ata1.00: configured for UDMA/100
[   37.029866] usb 1-3: configuration #1 chosen from 1 choice
[   37.509817] ata2.00: ATAPI: IDE DVD-ROM 16X, VER 2.40, max UDMA/33
[   37.509847] ata2.01: ATAPI: LITE-ON LTR-32123S, XS0U, max UDMA/33
[   37.632962] usbcore: registered new interface driver libusual
[   37.644389] Initializing USB Mass Storage driver...
[   37.646433] scsi2 : SCSI emulation for USB Mass Storage devices
[   37.647214] usbcore: registered new interface driver usb-storage
[   37.647222] USB Mass Storage support registered.
[   37.647405] usb-storage: device found at 2
[   37.647409] usb-storage: waiting for device to settle before scanning
[   37.674072] ata2.00: configured for UDMA/33
[   37.845243] ata2.01: configured for UDMA/33
[   37.845478] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[   37.846430] scsi 1:0:0:0: CD-ROM            IDE      DVD-ROM 16X      2.40 PQ: 0 ANSI: 5
[   37.851577] scsi 1:0:1:0: CD-ROM            LITE-ON  LTR-32123S       XS0U PQ: 0 ANSI: 5
[   37.867292] Driver 'sd' needs updating - please use bus_type methods
[   37.867463] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[   37.867489] sd 0:0:0:0: [sda] Write Protect is off
[   37.867493] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.867523] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.867605] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors (41110 MB)
[   37.867622] sd 0:0:0:0: [sda] Write Protect is off
[   37.867625] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.867651] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.867656]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   39.470851]  sda1 sda2 < sda5 >
[   39.504351] sd 0:0:0:0: [sda] Attached SCSI disk
[   39.515214] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.515249] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   39.515277] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   39.516499] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   39.516509] Uniform CD-ROM driver Revision: 3.20
[   39.516594] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   39.592316] sr1: scsi3-mmc drive: 111x/40x writer cd/rw xa/form2 cdda tray
[   39.592433] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   39.782714] Attempting manual resume
[   39.782723] swsusp: Resume From Partition 8:5
[   39.782725] PM: Checking swsusp image.
[   39.783155] PM: Resume from disk failed.
[   39.809486] EXT3-fs: INFO: recovery required on readonly filesystem.
[   39.809494] EXT3-fs: write access will be enabled during recovery.
[   42.642595] usb-storage: device scan complete
[   42.649561] scsi 2:0:0:0: Direct-Access     SMI      USB DISK         1100 PQ: 0 ANSI: 0 CCS
[   42.664597] sd 2:0:0:0: [sdb] 1966080 512-byte hardware sectors (1007 MB)
[   42.671535] sd 2:0:0:0: [sdb] Write Protect is off
[   42.671546] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   42.671551] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   42.697501] sd 2:0:0:0: [sdb] 1966080 512-byte hardware sectors (1007 MB)
[   42.704479] sd 2:0:0:0: [sdb] Write Protect is off
[   42.704485] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   42.704489] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   42.704500]  sdb: sdb1
[   42.714681] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   42.714768] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   48.568283] kjournald starting.  Commit interval 5 seconds
[   48.568328] EXT3-fs: sda1: orphan cleanup on readonly fs
[   48.568342] ext3_orphan_cleanup: deleting unreferenced inode 1802402
[   48.568446] ext3_orphan_cleanup: deleting unreferenced inode 213119
[   48.568487] ext3_orphan_cleanup: deleting unreferenced inode 2965523
[   48.568501] EXT3-fs: sda1: 3 orphan inodes deleted
[   48.568504] EXT3-fs: recovery complete.
[   48.811159] EXT3-fs: mounted filesystem with ordered data mode.
[   61.467029] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   62.155777] Linux agpgart interface v0.102
[   62.215738] agpgart: Detected SiS chipset - id:1845
[   62.220663] agpgart: AGP aperture is 64M @ 0xd0000000
[   62.262666] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.315797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.520698] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   62.582457] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   63.185883] input: Power Button (FF) as /devices/virtual/input/input3
[   63.201854] ACPI: Power Button (FF) [PWRF]
[   63.202052] input: Sleep Button (CM) as /devices/virtual/input/input4
[   63.217859] ACPI: Sleep Button (CM) [SLPB]
[   63.273097] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   63.322866] phy0: Selected rate control algorithm 'simple'
[   65.445827] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   65.459136] parport_pc 00:0a: reported by Plug and Play ACPI
[   65.459197] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   65.597690] nvidia: module license 'NVIDIA' taints kernel.
[   66.820858] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   66.820867] PCI: setting IRQ 5 as level-triggered
[   66.820872] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   66.822082] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   66.844162] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   66.844171] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   67.170849] intel8x0_measure_ac97_clock: measured 55821 usecs
[   67.170857] intel8x0: clocking to 48000
[   69.337666] udev: renamed network interface wlan0 to ra0
[   69.899316] lp0: using parport0 (interrupt-driven).
[   69.937962] it87: Found IT8705F chip at 0x290, revision 2
[   70.417216] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   71.003438] EXT3 FS on sda1, internal journal
[   72.429982] ip_tables: (C) 2000-2006 Netfilter Core Team
[   73.176856] No dock devices found.
[   79.812556] ppdev: user-space parallel port driver
[   80.167647] audit(1209325656.414:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5221 profile="/usr/sbin/cupsd" namespace="default"
[   80.197390] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   80.197423] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   80.197454] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   80.323092] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   80.323102] apm: overridden by ACPI.
[   83.525274] Bluetooth: Core ver 2.11
[   83.526981] NET: Registered protocol family 31
[   83.526990] Bluetooth: HCI device and connection manager initialized
[   83.526997] Bluetooth: HCI socket layer initialized
[   83.594484] Bluetooth: L2CAP ver 2.9
[   83.594494] Bluetooth: L2CAP socket layer initialized
[   83.758841] Bluetooth: RFCOMM socket layer initialized
[   83.758883] Bluetooth: RFCOMM TTY layer initialized
[   83.758886] Bluetooth: RFCOMM ver 1.8
[   93.489838] NET: Registered protocol family 10
[   93.491057] lo: Disabled Privacy Extensions
[   93.492250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   93.493551] ADDRCONF(NETDEV_UP): ra0: link is not ready
[  112.952212] end_request: I/O error, dev fd0, sector 0
[  113.000174] end_request: I/O error, dev fd0, sector 0
[  113.249868] UDF-fs: No partition found (1)
[  113.988217] ISOFS: Unable to identify CD-ROM format.
[  146.565940] NET: Registered protocol family 17
[  147.563637] ra0: Initial auth_alg=0
[  147.563652] ra0: authenticate with AP 00:18:4d:3e:c9:a6
[  147.565008] ra0: RX authentication from 00:18:4d:3e:c9:a6 (alg=0 transaction=2 status=0)
[  147.565014] ra0: authenticated
[  147.565018] ra0: associate with AP 00:18:4d:3e:c9:a6
[  147.566843] ra0: RX AssocResp from 00:18:4d:3e:c9:a6 (capab=0x411 status=0 aid=1)
[  147.566849] ra0: associated
[  147.567166] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[  158.349844] ra0: no IPv6 routers present
[  176.352227] ra0: no IPv6 routers present

```

This is with the USB drive plugged in, but not mounted. Thank you all for your help!

---

### Post by harshil102 on 2008-04-27
i am having the same problem but with a few twists. When i insert my usb drive, a device called "USB Drive" comes up in computer, but cannot be mounted, but in addition, there is also a device called "CD-R Drive" that comes up. I can like the other 2 people mount the USB Drive from CLI, but unlike them in my dmesg, there are no errors related to this usb drive that i can see.

my dmesg: ```
[   10.802116]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   10.802118] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.802157] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.882104] Calibrating delay using timer specific routine.. 4405.11 BogoMIPS (lpj=8810223)
[   10.882138] Security Framework initialized
[   10.882142] SELinux:  Disabled at boot.
[   10.882154] AppArmor: AppArmor initialized
[   10.882157] Failure registering capabilities with primary security module.
[   10.882165] Mount-cache hash table entries: 512
[   10.882263] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   10.882270] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.882272] CPU: L2 Cache: 512K (64 bytes/line)
[   10.882275] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   10.882282] Compat vDSO mapped to ffffe000.
[   10.882291] Checking 'hlt' instruction... OK.
[   10.898317] SMP alternatives: switching to UP code
[   10.899216] Freeing SMP alternatives: 11k freed
[   10.899314] Early unpacking initramfs... done
[   11.192749] ACPI: Core revision 20070126
[   11.192802] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.195656] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[   11.195679] Total of 1 processors activated (4405.11 BogoMIPS).
[   11.196181] ENABLING IO-APIC IRQs
[   11.196504] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   11.341677] Brought up 1 CPUs
[   11.341725] CPU0 attaching sched-domain:
[   11.341727]  domain 0: span 01
[   11.341729]   groups: 01
[   11.341868] net_namespace: 64 bytes
[   11.341873] Booting paravirtualized kernel on bare hardware
[   11.342281] Time: 16:49:14  Date: 04/27/08
[   11.342302] NET: Registered protocol family 16
[   11.342433] EISA bus registered
[   11.342465] ACPI: bus type pci registered
[   11.350096] PCI: PCI BIOS revision 2.10 entry at 0xfb730, last bus=1
[   11.350098] PCI: Using configuration type 1
[   11.350100] Setting up standard PCI resources
[   11.353679] ACPI: EC: Look up EC in DSDT
[   11.357748] ACPI: Interpreter enabled
[   11.357754] ACPI: (supports S0 S1 S3 S4 S5)
[   11.357768] ACPI: Using IOAPIC for interrupt routing
[   11.362401] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.363274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.406544] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   11.406662] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   11.406780] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   11.406885] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   11.406987] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   11.407086] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   11.407184] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   11.407282] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   11.407404] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   11.407516] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   11.407629] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   11.407759] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   11.407839] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.407860] pnp: PnP ACPI init
[   11.407866] ACPI: bus type pnp registered
[   11.410807] pnp: PnP ACPI: found 12 devices
[   11.410809] ACPI: ACPI bus type pnp unregistered
[   11.410811] PnPBIOS: Disabled by ACPI PNP
[   11.410962] PCI: Using ACPI for IRQ routing
[   11.410964] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.453531] NET: Registered protocol family 8
[   11.453533] NET: Registered protocol family 20
[   11.453586] AppArmor: AppArmor Filesystem Enabled
[   11.457521] Time: tsc clocksource has been installed.
[   11.465538] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   11.465540] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   11.465543] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   11.465545] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   11.465547] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   11.465550] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   11.465552] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   11.465554] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[   11.465557] system 00:00: iomem range 0x0-0x0 could not be reserved
[   11.465559] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   11.465561] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   11.465564] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[   11.465568] system 00:02: ioport range 0x4000-0x407f has been reserved
[   11.465571] system 00:02: ioport range 0x5000-0x500f has been reserved
[   11.465575] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   11.465578] system 00:03: ioport range 0x800-0x805 has been reserved
[   11.465580] system 00:03: ioport range 0x290-0x297 has been reserved
[   11.495839] PCI: Bridge: 0000:00:01.0
[   11.495841]   IO window: a000-afff
[   11.495845]   MEM window: c0000000-dfffffff
[   11.495847]   PREFETCH window: 50000000-500fffff
[   11.495861] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.495871] NET: Registered protocol family 2
[   11.533516] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.533793] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.534724] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.535204] TCP: Hash tables configured (established 131072 bind 65536)
[   11.535207] TCP reno registered
[   11.545565] checking if image is initramfs... it is
[   11.996975] Switched to high resolution mode on CPU 0
[   12.108648] Freeing initrd memory: 7656k freed
[   12.109129] audit: initializing netlink socket (disabled)
[   12.109143] audit(1209314954.204:1): initialized
[   12.109264] highmem bounce pool size: 64 pages
[   12.110570] VFS: Disk quotas dquot_6.5.1
[   12.110622] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.110725] io scheduler noop registered
[   12.110727] io scheduler anticipatory registered
[   12.110729] io scheduler deadline registered
[   12.110737] io scheduler cfq registered (default)
[   12.110751] PCI: VIA PCI bridge detected. Disabling DAC.
[   12.110816] Boot video device is 0000:01:00.0
[   12.111006] isapnp: Scanning for PnP cards...
[   12.464938] isapnp: No Plug & Play device found
[   12.485220] Real Time Clock Driver v1.12ac
[   12.485294] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.485396] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.485862] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.486384] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.486435] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.486502] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[   12.486504] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   12.486870] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.486874] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.496445] mice: PS/2 mouse device common for all mice
[   12.496528] EISA: Probing bus 0 at eisa.0
[   12.496545] Cannot allocate resource for EISA slot 4
[   12.496547] Cannot allocate resource for EISA slot 5
[   12.496559] EISA: Detected 0 cards.
[   12.496562] cpuidle: using governor ladder
[   12.496563] cpuidle: using governor menu
[   12.496639] NET: Registered protocol family 1
[   12.496658] Using IPI No-Shortcut mode
[   12.496690] registered taskstats version 1
[   12.496777]   Magic number: 4:501:844
[   12.496902]   hash matches device ptyrd
[   12.496953] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.496955] EDD information not available.
[   12.497222] Freeing unused kernel memory: 364k freed
[   13.713983] fuse init (API version 7.9)
[   13.810985] ACPI: Thermal Zone [THRM] (46 C)
[   14.346536] SCSI subsystem initialized
[   14.390302] libata version 3.00 loaded.
[   14.418323] usbcore: registered new interface driver usbfs
[   14.418343] usbcore: registered new interface driver hub
[   14.438279] usbcore: registered new device driver usb
[   14.442497] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   14.442505] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   14.442559] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   14.442577] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   14.442595] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   14.456514] sata_via 0000:00:0f.0: version 2.3
[   14.456533] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   14.456573] sata_via 0000:00:0f.0: routed to hard irq line 11
[   14.466204] scsi0 : sata_via
[   14.484863] scsi1 : sata_via
[   14.484914] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xb400 bmdma 0xc000 irq 16
[   14.484916] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc008 irq 16
[   14.497563] USB Universal Host Controller Interface driver v3.0
[   14.524296] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   14.622146] Floppy drive(s): fd0 is 1.44M
[   14.645608] FDC 0 is a post-1991 82077
[   14.685972] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   14.867247] ata1.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[   14.867251] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   14.883015] ata1.00: configured for UDMA/133
[   15.085493] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   15.096236] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-2 05.0 PQ: 0 ANSI: 5
[   15.096619] pata_via 0000:00:0f.1: version 0.3.3
[   15.096641] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   15.097499] scsi2 : pata_via
[   15.097926] scsi3 : pata_via
[   15.099001] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xc800 irq 14
[   15.099004] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xc808 irq 15
[   15.104912] Driver 'sd' needs updating - please use bus_type methods
[   15.104982] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   15.104992] sd 0:0:0:0: [sda] Write Protect is off
[   15.104995] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.105007] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.105043] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   15.105049] sd 0:0:0:0: [sda] Write Protect is off
[   15.105051] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.105062] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.105064]  sda: sda1 sda2 sda3 sda4
[   15.134175] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.139703] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.261919] ata3.00: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
[   15.261924] ata3.00: 240121728 sectors, multi 16: LBA 
[   15.277648] ata3.00: configured for UDMA/133
[   15.399929] Attempting manual resume
[   15.399933] swsusp: Resume From Partition 8:4
[   15.399934] PM: Checking swsusp image.
[   15.400177] PM: Resume from disk failed.
[   15.408028] JFS: nTxBlock = 8089, nTxLock = 64712
[   15.761332] ata4.00: ATAPI: SONY    DVD RW DRU-810A, 1.0f, max UDMA/33
[   15.761350] ata4.01: ATAPI: ATAPI   CD-RW 52X24, F.FZ, max UDMA/33
[   15.932999] ata4.00: configured for UDMA/33
[   16.104651] ata4.01: configured for UDMA/33
[   16.104742] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
[   16.104805] sd 2:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   16.104814] sd 2:0:0:0: [sdb] Write Protect is off
[   16.104816] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   16.104828] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.104866] sd 2:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   16.104873] sd 2:0:0:0: [sdb] Write Protect is off
[   16.104875] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   16.104885] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.104888]  sdb: sdb1
[   16.107892] sd 2:0:0:0: [sdb] Attached SCSI disk
[   16.107913] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   16.109997] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-810A  1.0f PQ: 0 ANSI: 5
[   16.110041] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[   16.110449] scsi 3:0:1:0: CD-ROM            ATAPI    CD-RW 52X24      F.FZ PQ: 0 ANSI: 5
[   16.110487] scsi 3:0:1:0: Attached scsi generic sg3 type 5
[   16.110808] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   16.110814] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   16.110824] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   16.111077] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   16.111106] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000cc00
[   16.111210] usb usb1: configuration #1 chosen from 1 choice
[   16.111228] hub 1-0:1.0: USB hub found
[   16.111232] hub 1-0:1.0: 2 ports detected
[   16.212345] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   16.212358] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   16.212378] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   16.212399] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d000
[   16.212485] usb usb2: configuration #1 chosen from 1 choice
[   16.212502] hub 2-0:1.0: USB hub found
[   16.212506] hub 2-0:1.0: 2 ports detected
[   16.316251] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   16.316265] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   16.316283] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   16.316304] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d400
[   16.316396] usb usb3: configuration #1 chosen from 1 choice
[   16.316413] hub 3-0:1.0: USB hub found
[   16.316418] hub 3-0:1.0: 2 ports detected
[   16.420110] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   16.420122] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   16.420141] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   16.420163] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d800
[   16.420252] usb usb4: configuration #1 chosen from 1 choice
[   16.420273] hub 4-0:1.0: USB hub found
[   16.420277] hub 4-0:1.0: 2 ports detected
[   16.451981] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   16.524090] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   16.524103] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   16.524123] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   16.524160] ehci_hcd 0000:00:10.4: irq 17, io mem 0xe0000000
[   16.579880] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.579981] usb usb5: configuration #1 chosen from 1 choice
[   16.579999] hub 5-0:1.0: USB hub found
[   16.580005] hub 5-0:1.0: 8 ports detected
[   16.684208] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   16.684217] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   16.688330] eth0: VIA Rhine II at 0xe0001000, 00:14:2a:cd:cb:87, IRQ 18.
[   16.689038] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   16.975405] usb 1-1: device not accepting address 2, error -71
[   18.717457] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   18.913719] usb 1-1: configuration #1 chosen from 1 choice
[   19.156991] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   19.364169] usb 1-2: configuration #1 chosen from 1 choice
[   19.644439] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   19.982843] usb 3-1: configuration #1 chosen from 1 choice
[   21.053424] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   21.309327] Linux agpgart interface v0.102
[   21.338175] agpgart: Detected AGP bridge 0
[   21.346048] agpgart: AGP aperture is 256M @ 0xb0000000
[   21.433835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.462504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.574800] input: Power Button (FF) as /devices/virtual/input/input2
[   21.618288] ACPI: Power Button (FF) [PWRF]
[   21.618348] input: Power Button (CM) as /devices/virtual/input/input3
[   21.646243] ACPI: Power Button (CM) [PWRB]
[   21.973125] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   21.998706] parport_pc 00:0a: reported by Plug and Play ACPI
[   21.998776] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.714502] Driver 'sr' needs updating - please use bus_type methods
[   22.726595] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   22.726600] Uniform CD-ROM driver Revision: 3.20
[   22.726662] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   22.733007] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   22.733096] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   22.866246] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   23.032309] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   23.032338] [fglrx] ASYNCIO init succeed!
[   23.032466] [fglrx] PAT is enabled successfully!
[   23.033047] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   23.256657] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   23.256666] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 19
[   23.256802] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   23.332739] usbcore: registered new interface driver hiddev
[   23.723661] hiddev96hidraw0: USB HID v1.10 Device [APC Back-UPS ES 725 FW:802.n5.D USB FW:n5] on usb-0000:00:10.0-1
[   23.755732] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input5
[   23.783896] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:10.0-2
[   23.808007] input: Jess Tech GGE909 PC Recoil Pad as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/input/input6
[   23.819871] input,hidraw2: USB HID v1.10 Joystick [Jess Tech GGE909 PC Recoil Pad] on usb-0000:00:10.2-1
[   23.819887] usbcore: registered new interface driver usbhid
[   23.819891] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.967812] lp0: using parport0 (interrupt-driven).
[   26.144563] Adding 2136636k swap on /dev/sda4.  Priority:-1 extents:1 across:2136636k
[   27.736693] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   27.739676] SGI XFS Quota Management subsystem
[   27.785800] XFS mounting filesystem sda3
[   27.848910] Ending clean XFS mount for filesystem: sda3
[   29.046177] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.100188] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   30.100211] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   30.106162] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   30.138322] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   30.385772] No dock devices found.
[   32.770297] ppdev: user-space parallel port driver
[   33.256693] audit(1209329376.430:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4772 profile="/usr/sbin/cupsd" namespace="default"
[   34.573965] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   37.296732] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   38.283742] NET: Registered protocol family 17
[   39.677072] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   39.677079] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   39.677083] [fglrx] AGP detected, AgpState   = 0x1f000a0b (hardware caps of chipset)
[   39.679081] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   39.679656] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.680263] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   39.680813] [fglrx] AGP enabled,  AgpCommand = 0x1f000302 (selected caps)
[   39.881618] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   39.881624] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   39.881626] [fglrx] Reserve Block - 2 offset =  0X1ffff000 length = 0X1000
[   39.881629] [fglrx] Reserve Block - 3 offset =  0Xff80000 length = 0X80000
[   40.002340] [fglrx] interrupt source 10000000 successfully enabled
[   40.002346] [fglrx] enable ID = 0x00000008
[   40.003278] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  258.839335] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  258.972089] usb 5-6: configuration #1 chosen from 1 choice
[  259.048561] usbcore: registered new interface driver libusual
[  259.087774] Initializing USB Mass Storage driver...
[  259.093415] scsi4 : SCSI emulation for USB Mass Storage devices
[  259.095227] usbcore: registered new interface driver usb-storage
[  259.095234] USB Mass Storage support registered.
[  259.096549] usb-storage: device found at 5
[  259.096551] usb-storage: waiting for device to settle before scanning
[  264.089653] usb-storage: device scan complete
[  264.090272] scsi 4:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0 CCS
[  264.090761] scsi 4:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0
[  264.100176] sd 4:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[  264.100875] sd 4:0:0:0: [sdc] Write Protect is off
[  264.100879] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  264.100881] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  264.103117] sd 4:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[  264.103762] sd 4:0:0:0: [sdc] Write Protect is off
[  264.103764] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  264.103766] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  264.103770]  sdc: sdc1
[  264.104899] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[  264.104935] sd 4:0:0:0: Attached scsi generic sg4 type 0
[  264.112109] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[  264.112163] sr 4:0:0:1: Attached scsi CD-ROM sr2
[  264.112200] sr 4:0:0:1: Attached scsi generic sg5 type 5
[  923.433145] end_request: I/O error, dev fd0, sector 0
[  927.657376] usb 5-6: USB disconnect, address 5
[  930.437362] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  930.570105] usb 5-6: configuration #1 chosen from 1 choice
[  930.577957] scsi5 : SCSI emulation for USB Mass Storage devices
[  930.585914] usb-storage: device found at 6
[  930.585919] usb-storage: waiting for device to settle before scanning
[  935.579786] usb-storage: device scan complete
[  935.580404] scsi 5:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0 CCS
[  935.580892] scsi 5:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0
[  935.590412] sd 5:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[  935.591129] sd 5:0:0:0: [sdc] Write Protect is off
[  935.591133] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  935.591135] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  935.593249] sd 5:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[  935.593888] sd 5:0:0:0: [sdc] Write Protect is off
[  935.593891] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  935.593893] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  935.593896]  sdc: sdc1
[  935.595031] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[  935.595069] sd 5:0:0:0: Attached scsi generic sg4 type 0
[  935.602240] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[  935.602299] sr 5:0:0:1: Attached scsi CD-ROM sr2
[  935.602332] sr 5:0:0:1: Attached scsi generic sg5 type 5
[ 1467.749977] usb 5-6: USB disconnect, address 6
[ 1469.142938] usb 5-6: new high speed USB device using ehci_hcd and address 7
[ 1469.275687] usb 5-6: configuration #1 chosen from 1 choice
[ 1469.283096] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1469.291531] usb-storage: device found at 7
[ 1469.291535] usb-storage: waiting for device to settle before scanning
[ 1474.285374] usb-storage: device scan complete
[ 1474.285928] scsi 6:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0 CCS
[ 1474.286359] scsi 6:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0
[ 1474.293486] sd 6:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[ 1474.294090] sd 6:0:0:0: [sdc] Write Protect is off
[ 1474.294093] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 1474.294095] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1474.296215] sd 6:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[ 1474.296843] sd 6:0:0:0: [sdc] Write Protect is off
[ 1474.296845] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 1474.296847] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1474.296851]  sdc: sdc1
[ 1474.297995] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 1474.298028] sd 6:0:0:0: Attached scsi generic sg4 type 0
[ 1474.307207] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1474.307261] sr 6:0:0:1: Attached scsi CD-ROM sr2
[ 1474.307295] sr 6:0:0:1: Attached scsi generic sg5 type 5
[ 1484.917664] usb 5-6: USB disconnect, address 7
[ 1488.277680] usb 5-6: new high speed USB device using ehci_hcd and address 8
[ 1488.410517] usb 5-6: configuration #1 chosen from 1 choice
[ 1488.418004] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1488.426280] usb-storage: device found at 8
[ 1488.426284] usb-storage: waiting for device to settle before scanning
[ 1493.420072] usb-storage: device scan complete
[ 1493.420690] scsi 7:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0 CCS
[ 1493.421177] scsi 7:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.51 PQ: 0 ANSI: 0
[ 1493.430577] sd 7:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[ 1493.431292] sd 7:0:0:0: [sdc] Write Protect is off
[ 1493.431295] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 1493.431298] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1493.433535] sd 7:0:0:0: [sdc] 1944383 512-byte hardware sectors (996 MB)
[ 1493.434174] sd 7:0:0:0: [sdc] Write Protect is off
[ 1493.434176] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 1493.434178] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1493.434182]  sdc: sdc1
[ 1493.435311] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 1493.435348] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 1493.442525] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1493.442587] sr 7:0:0:1: Attached scsi CD-ROM sr2
[ 1493.442622] sr 7:0:0:1: Attached scsi generic sg5 type 5
```

---

### Post by Bloch on 2008-04-27
I have the same problem.

My pendrives no longer automount. The name of the device "Lexar Media" appears in the left pane in Nautilus and I get the message
Invalid mount option when attempting to mount the volume 'LEXAR MEDIA'.

Similarly with my second pendrive.

They both automounted under gutsy.

---

### Post by Daniel15 on 2008-04-27
> **danwood76 said:**
> Adding USB disks to the fstab stops hal from automounting it.
Unless the disk is attatched when you boot up.

It looks like, from your demsg output, that your USB disk is incorrectly partitioned, and the hal is trying to access data past the end of the disk.

What you could do is mount it manually then copy all the data off it (as its only 4GB right?) and reformat and repartition the USB drive.
Then try re plugging it.

Okay, thanks for that. I'll try to reformat it tonight (I'm at uni at the moment... At least the wireless is still working fine :D)

Yeah, it's a 4 GB MP3 player, but some space seems to be reserved for the system (so the available space is less than that). I haven't formatted it, so maybe it was formatted wrong at the factory? I dunno. :P

---

### Post by danwood76 on 2008-04-28
Hmmm, seems odd that the factory would have formatted it incorrectly.

Did you all Upgrade to hardy through the synaptic route (update manager)?
Im wondering if its another upgrade bug, if you all did I would produce a bug report for the community to fix.

---

### Post by Bloch on 2008-04-28
CDs and other devices automount as normal.

My usb pendrives return the error message 
> Cannot mount volume.
Invalid mount option when attempting to mount the volume.

I upgraded from gutsy to hardy via update manager. 
My fstab refers solely to the hard drive and cd/dvd drives, so I don't think the problem lies there.

Anyone know where these "mount options" are stored??

---

### Post by Bloch on 2008-04-28
I have found a solution which so far appears to work.

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)


Open Applications > System Tools > Configuration Editor

Go to the key system > storage > default_options > vfat
Edit the mount_options key by removing the usefree option.

Reboot. (Not sure if this step is absolutely neccessary) 
Now my pendrives are automounted.


This entry in the bug report above seems to explain things.
Can others confirm if this works?
> This bug was fixed in the package gnome-mount - 0.7-2ubuntu2

---------------
gnome-mount (0.7-2ubuntu2) hardy; urgency=low

  * debian/patches/ubuntu-default-mount-options.patch: Drop VFAT option
    'usefree', it's not necessary any more with the current Hardy kernel,
    and incompatible with pre-gutsy kernels. (LP: #151025)

 -- Martin Pitt <email address hidden> Mon, 03 Mar 2008 15:54:25 +0100



---

### Post by abobov on 2008-04-28
> **Bloch said:**
> Can others confirm if this works?

This work for me too. Reboot not neccessary.

---

### Post by tiagofaq on 2008-04-28
I just installed a fresh copy of Hardy desktop x64 version, and I don't see any usefree option in mount_options key.

However running the following commnand works:

```
lsusb
```

I dont know why, I came across this by accident.

I have to run lsusb whenever I want to mount the device. I moved files in and out and it works fine.

Here is an extract of my dmesg with me connecting the mp3 player, hardy failling to dectect and the after the scan made by lsusb properly mounting

```
[42672.285744] usb 5-2: new high speed USB device using ehci_hcd and address 8
[42674.636153] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[42674.636165] hub 5-0:1.0: hub_port_status failed (err = -32)
[42679.574578] usb 5-2: new high speed USB device using ehci_hcd and address 9
[42679.719706] usb 5-2: configuration #1 chosen from 1 choice
[42679.727003] scsi3 : SCSI emulation for USB Mass Storage devices
[42679.727379] usb-storage: device found at 9
[42679.727382] usb-storage: waiting for device to settle before scanning
[42680.276118] usb-storage: device scan complete
[42680.277348] scsi 3:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v01. PQ: 0 ANSI: 0
[42680.279205] sd 3:0:0:0: [sdb] 3992576 512-byte hardware sectors (2044 MB)
[42680.279831] sd 3:0:0:0: [sdb] Write Protect is off
[42680.279837] sd 3:0:0:0: [sdb] Mode Sense: 04 00 00 00
[42680.279841] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42680.282073] sd 3:0:0:0: [sdb] 3992576 512-byte hardware sectors (2044 MB)
[42680.282699] sd 3:0:0:0: [sdb] Write Protect is off
[42680.282704] sd 3:0:0:0: [sdb] Mode Sense: 04 00 00 00
[42680.282707] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42680.282714]  sdb: unknown partition table
[42680.289110] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[42680.289184] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by CazperII on 2008-04-30
Since I updated my machine to 8.04 automounting of USB-drives also broke down. Dmesg shows that the drive is detected but the drives aren't mounted. 

The option usefree doesn't appear to be in the vfat options, and lsusb doesn't change anything. I also tried restarting the HAL daemon but to no avail. 

I'm running Ubuntu 8.04 AMD64, manually mounting the drives works fine. 

Anyone got more idea's how to fix it?

---

### Post by wariskampar on 2008-04-30
I also have the same problem. Ubuntu fail to auto detect my IPOD. Currently I use Wubi to install Ubuntu. Somebody mention about Configuration Editor but I can not find it anywhere. 

(Off topic but in order to get accurate assistance, i need to tell) I'm total noob and dont understand any single word you guys were talking here. But i'm passionate to migrate from XP Home other than 'USB not working'. More over, Command Prompt(Windows Term) really scared me, it seems like Ubuntu use a lot of it.

edit; somehow i manage to find Config Editor. But similar to a post above me, there is no usefree key. lsusb doestnt work either

---

### Post by Holzster on 2008-04-30
> **tiagofaq said:**
> I just installed a fresh copy of Hardy desktop x64 version, and I don't see any usefree option in mount_options key.

However running the following commnand works:

```
lsusb
```

I dont know why, I came across this by accident.

I have to run lsusb whenever I want to mount the device. I moved files in and out and it works fine.

Here is an extract of my dmesg with me connecting the mp3 player, hardy failling to dectect and the after the scan made by lsusb properly mounting

```
[42672.285744] usb 5-2: new high speed USB device using ehci_hcd and address 8
[42674.636153] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[42674.636165] hub 5-0:1.0: hub_port_status failed (err = -32)
[42679.574578] usb 5-2: new high speed USB device using ehci_hcd and address 9
[42679.719706] usb 5-2: configuration #1 chosen from 1 choice
[42679.727003] scsi3 : SCSI emulation for USB Mass Storage devices
[42679.727379] usb-storage: device found at 9
[42679.727382] usb-storage: waiting for device to settle before scanning
[42680.276118] usb-storage: device scan complete
[42680.277348] scsi 3:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v01. PQ: 0 ANSI: 0
[42680.279205] sd 3:0:0:0: [sdb] 3992576 512-byte hardware sectors (2044 MB)
[42680.279831] sd 3:0:0:0: [sdb] Write Protect is off
[42680.279837] sd 3:0:0:0: [sdb] Mode Sense: 04 00 00 00
[42680.279841] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42680.282073] sd 3:0:0:0: [sdb] 3992576 512-byte hardware sectors (2044 MB)
[42680.282699] sd 3:0:0:0: [sdb] Write Protect is off
[42680.282704] sd 3:0:0:0: [sdb] Mode Sense: 04 00 00 00
[42680.282707] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42680.282714]  sdb: unknown partition table
[42680.289110] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[42680.289184] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

tiagofaq

thanks the lsusb worked thanks!!

---

### Post by danwood76 on 2008-05-01
That lsusb solution sounds like its not probing for new USB devices.
Sounds like a definate bug.

File a bug report so the devs can fix it.

---

### Post by yellowbread on 2008-05-01
I don't know if this will have any bearing on the problems being discussed here, but I have had a similar problem. The device affected is a USB thumb drive. The drive has 4 partitions and is used for installing various versions of hardy. The first partition is a big fat 32 partition so that I can use the thing in windows machines, then a super grub partition, then files for installing 64 bit hardy, then files for installing 32 bit hardy.

If I install 64 bit hardy on a machine from the third partition, then that third partition does not mount on that machine with the same errors mentioned in other posts in this thread:

```
Cannot mount volume.
Invalid mount option when attempting to mount the volume.
```

This is the fstab from that machine:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=828119da-e674-4e58-add0-241132c4274c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=c35705e8-ef8f-4837-a303-9a7ed0048b06 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=0a55c19c-cfc3-41f8-a1cd-702503a88125 /media/Gutsy    ext3    relatime        0       2
# /dev/sda4
UUID=D0DC3593DC3574B6 /media/WindowsData ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4a48be5f-3f29-4658-b5d0-9cced5969190 /media/hardybeta ext3    relatime        0       2
# /dev/sdb2
UUID=bbef68bc-4510-4a31-a436-9c12d052181a none            swap    sw              0       0
/dev/sdd3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

As you can see, it's trying to mount the third partition of sdd as a cdrom. Commenting out this line fixes the problem with the third partition of the thumb drive not mounting when inserted. The same fix works for 32 bit installs and the 4th partition not mounting.

---

### Post by SteveOSupremo on 2008-05-01
> **danwood76 said:**
> Hmmm, seems odd that the factory would have formatted it incorrectly.

Did you all Upgrade to hardy through the synaptic route (update manager)?
Im wondering if its another upgrade bug, if you all did I would produce a bug report for the community to fix.

I'm currently reading through this thread I'm having the same problem.  all of my usb storage devices don't work.  I have a USB mouse that seems to be working but not the drives.

i haven't tried the CLI method (I'm verry new with Ubuntu)

I installed using the WUBI installer.

Steveo

---

### Post by MasterOfMuppets on 2008-05-02
I have this bug in KDE as well (NOT 4).
Seems to be able to mount it once in a while, and I can read the drive via GUI, but even right clicking in the drive's konqueror space unleashes havoc.
I have full access via CLI though. But I can't install rockbox, or upload my music into it, so it's a problem...

Tried lsusb. It displays the drive OK, with manufacturer name and all, but it doesn't really help.
In Gusty (sometimes I really feel like hitting myself hard over the head when I upgrade), HAL dealt with it just fine.

I filed a KDE bug report, since the bug linked here is just for GNOME...
[https://bugs.launchpad.net/ubuntu/+bug/225931]("https://bugs.launchpad.net/ubuntu/+bug/225931")

---

### Post by Daniel15 on 2008-05-02
Okay, the problem I originally reported in this topic was reported as a bug a while back, and I just noticed now: [https://bugs.launchpad.net/ubuntu/+bug/209483/](https://bugs.launchpad.net/ubuntu/+bug/209483/)

---

### Post by MasterOfMuppets on 2008-05-04
Well, doesn't seem like anything's moving, and this is a serious problem.
I'll look into the memory chips used by the sony players and compare them to my
sansa chips. Maybe it's just mal-implementation by them, and nothing is actually
wring with Ubuntu (and Gusty mounted them fine despite them being out of line?).

Updated my bug report with a link to the bug report you've given, Daniel.

---

### Post by MasterOfMuppets on 2008-05-04
Sorry, double post...

---

### Post by MasterOfMuppets on 2008-05-06
Fixed in an update!
:-)

---

### Post by razta on 2008-05-06
Still cant get mine to auto detect. :( Gotten used to mounting via CLI anyway.

---

### Post by u18b on 2008-05-10
I'm a newbie.  Installed Hardy 8.04 with updates and USB also doesn't work.



Here is a twist no one has mentioned yet.

USB drives work PERFECTLY when using the live USB edition.

So if I boot the Live edition off a CD or a USB stick,  then all of my USB sticks will mount fine without a single hitch.

But when I boot from the version of Ubuntu installed on my hard drive,  THAT is where all of the drive recognition breaks down.

This is very discouraging to a first-time Linux user wanting to jump the Micro$oft ship.  I keep data on the USB sticks and need access to them at all times.

---

### Post by VCSkier on 2008-05-12
I've got the same problem here on a Gateway notebook.  In addition to not automounting my USB flash drive, it won't automount my USB external hard drive, or my camera's SD card (via the card slot on this laptop).  This certainly is a disappointment for a LTS release.  I guess I should have waited for 8.04.1 for this system; I'm not the primary user and my wife is finding this quite frustrating.

A fix hasn't come down the update channel yet, but hopefully it will soon.  I don't have the "Pre-released updates (hardy-proposed)" repository enabled.  Could this have been where MasterOfPuppets got his fix?  I was under the impression that this repo could introduce untested and often problematic packages...  Any opinions?

---

### Post by CazperII on 2008-05-12
Yeah the recent update didn't fix my automount problem either. Since I upgraded I tried a Hardy live CD and automounting does work when booting in a live session. 

This tells me that it's probably an old setting remaining from Gutsy wich is causing the problem.

Also the command

```
gnome-mount -bd /dev/sdX 
```

Mounts the drive (replace X with your device). Because this is the command used by HAL to automount I guess there is a problem with the interprocess communication. 

Still no solution *sigh*

---

### Post by rockin_goliath on 2008-05-13
> **CazperII said:**
> Yeah the recent update didn't fix my auto mount problem either. Since I upgraded I tried a Hardy live CD and auto mounting does work when booting in a live session. 

This tells me that it's probably an old setting remaining from Gutsy wich is causing the problem.

I don't think this is the case, I think its a bug in a recent update. After doing a fresh installation of 8.04 Hardy, auto mounting works perfectly. After doing the updates and doing a reboot, auto mounting stops working. I have confirmed this twice. but haven't narrowed it down to what updates package is causing it. Possible HAL?

---

### Post by u18b on 2008-05-14
I still can't do anything.

lsusb does make contact with the USB stick.  But it does not mount anything.

$ sudo mount /dev/sdb1 /mnt/USB

did not work for me.


Nor did:
gnome-mount -bd /dev/sdb1

I'm running AMD 64 laptop with Hardy 8.04.  As stated before,  when booting off the Live CD,  everthing mounts perfectly.

I did make one further discovery.  I erased the Linux partition and started over.  Since all this worked on the Live CD, I wondered if the error was caused by an update.

So I started off again.  Loaded Hardy 8.04 off of the Live CD.  Once loaded, I did NOT update anything.  The very first thing I did was put a USB stick in--- it did NOT  work.

So the error is on the Live CD files as they are copied to the hard drive, and not a part of any update.



I hope they fix this soon.

---

### Post by u18b on 2008-05-15
I'm just a Newbie,  but I think I solved this problem.

Here is the full explanation of the bug.

[http://ubuntuforums.org/showthread.php?p=4962593](http://ubuntuforums.org/showthread.php?p=4962593)



Go to FSTAB and comment out the line that has SDB1 in it.

That should fix it.

---

### Post by gwpritch on 2008-05-15
> **razta said:**
> Im having the same problem with all my USB storage devices. Can mount via CLI using:

```
$ sudo mount /dev/sdb1 /mnt/USB
```

But it does not auto detect the USB drives and add the icon to the desktop when I plug it in. I know I could just run the mount command every time I wanted to use it but my girlfriend also uses this PC and hasn't a clue about the CLI.

Heres my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c4e6bf9b-7632-4dba-bc8c-572c950e372e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9d45d72a-a389-48c1-bfb4-3155b4145360 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0
/dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0
```

It autodetected in 7.10 but since I upgraded to 8.04, it doesnt seem to work.

Any ideas?

As long as you have the _noauto_ option on the USB line it is never going to automount for you and will have to be explicitly mounted :)

---

### Post by danwood76 on 2008-05-15
I will say this again, reitterating what I said in post 5.

Any Item in the fstab will only automount on boot.
Any item within the fstab will not automount when inserted with the system running, hal takes care of it then but if its in the fstab hal ignores it.

There is a bug concerning sony mp3 players, other bugs are probably due to fstab entries.

---

### Post by gwpritch on 2008-05-15
Let me reitterate...with the noauto option it won't automount even on boot. The only reason to have it in fstab is if you want to mount to a mount point of your choosing.

---

### Post by jeffrash on 2008-05-15
I had the same issue this morning.  Everything was working yesterday and then this morning it wasn't.  Odd.  

Anyway, I found just as you guys did that CLI mount worked fine.  I also checked my fstab, I had nothing in it for my IPOD or any other sdxx.  In the CLI I had to SUDO, so as a test I gave my user ID create/delete permissions to the /media folder and it started work in seconds.  I didn't even have to reboot.

I've rebooted several times today and the work around seems to be working.  Hope this helps someone.  Let me know if it does.  Good luck!

---

### Post by mike11 on 2008-05-16
I have the same problem, it worked on live cd, but after installing on hd, it won't mount flash drive, and I need it really :). But usb printer works ?!

---

### Post by u18b on 2008-05-16
So, for you guys still having problems,   have you guys tried my solution yet?

It has been a couple of days since my fix and my computer is still working perfectly. 

I'm just a newbie  (and thus I have a lot to learn about Linux), but I don't think you should have ANY reference to a device named SDB1  in fstab.   And  it will especially go wrong if such a device is listed as a CD-ROM.

If you are like me and loaded the Hardy 8.04 Live CD onto a USB drive.  And then you loaded the program onto your hard drive from a USB drive,  then I'm pretty certain you will see the same line in your FSTAB that someone posted above.  Look at it again:

/dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0


THIS is the offending line that is causing all the trouble.


Normally, the first USB device is going to be listed as sbd1.  But look on down that line and notice that FSTAB looks for volume properties of ISO9660.  Heck-  that's a CD-Rom.  That is the problem.  A USB stick is not a CD-Rom.   THIS is the bug in the install program that the programmers need to fix.  The install program ASSUMES that the install device MUST be a CD-Rom.

The solution to all these USB mounting problems, I believe,  is to simply comment out any line that starts out with  /dev/sbd1 ....  in it.

In fact, I guess you could delete it.  But the safe and cautious way would be to just comment out the line (or lines).  Add the pound sign in front of the line. like this:

#   /dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0


My fully working Hardy 8.04 that I re-installed off of the CD-Rom (not installed off a USB stick) has ZERO references to  /dev/sdb1  in fstab.


I HATE this bug.  But this solved it for me.  Hardy behaves normally now.

I can mount and eject USB sticks all day long.  Problem solved.

---

### Post by CazperII on 2008-05-17
Nope still got the problem. It's indeed an annoying bug, but it's just not enough to revert to 7.10. 

I'm still waiting for that magic update that fixes my automount problem. Maybe if I have the time I'll try a fresh install. 

My experience with dist upgrades is really bad. The first days after upgrading I'm always fixing annoying bugs, like the automount one.

---

### Post by jeffrash on 2008-05-17
OK, the permissions I talked about before don't work after all.  I am still having the issue, but I have found something else that I just can't understand.  

If I'm not connected to the network it works, every time.

If I'm connected at home on my open wireless access point with NAT'd internet access it works, every time.

If I'm connected at work on our WPA-2 / PEAP secured network with Proxy'd internet access it doesn't work, ever.

I can reproduce this at will.  Anyone have any ideas?

BTW, this is my IPOD, I will test another USB storage device Monday at work.

---

### Post by mattmook on 2008-05-21
This post solved the problem for me - patching how hal handles a particular error situation:

[https://bugs.launchpad.net/ubuntu/+bug/209483/comments/42](https://bugs.launchpad.net/ubuntu/+bug/209483/comments/42)


Regards,

Matt

---

### Post by n-alexander on 2008-05-23
looks like a HAL issue. I'm trying to find HAL config files for mounting, those must be XML files with options per FS type. Any ideas where to look?

---

### Post by Tamale on 2008-06-13
This is a ridiculous problem for a supposedly 'hardy' release!!

why isn't this at the top of the critical bug lists?


I had this problem too, and two things worked for me...

the lsusb trick worked great for a band-aid.. (plug in drive, get mount error message, unplug, type lsusb, plug in drive, works)

but the bigger problem is indeed the extra line in the fstab.  why is this line being created?  someone needs to figure this out asap and fix it.

once i commented it out and rebooted, the drive was recognized first try every time.

---

### Post by u18b on 2008-06-22
Tamale,

I'm glad you confirmed my findings.  No one else has.

There must be multiple sources for this bug since others tried what I suggested and it did not work for them.

I'm glad it worked for you.

I was debating whether to permanently go to Ubuntu and abandon Vista.  This stupid bug was almost a deal-breaker.

---

### Post by oliwek on 2008-07-24
> **u18b said:**
> So, for you guys still having problems,   have you guys tried my solution yet?

It has been a couple of days since my fix and my computer is still working perfectly. 

I'm just a newbie  (and thus I have a lot to learn about Linux), but I don't think you should have ANY reference to a device named SDB1  in fstab.   And  it will especially go wrong if such a device is listed as a CD-ROM.

If you are like me and loaded the Hardy 8.04 Live CD onto a USB drive.  And then you loaded the program onto your hard drive from a USB drive,  then I'm pretty certain you will see the same line in your FSTAB that someone posted above.  Look at it again:

/dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0


THIS is the offending line that is causing all the trouble.


Normally, the first USB device is going to be listed as sbd1.  But look on down that line and notice that FSTAB looks for volume properties of ISO9660.  Heck-  that's a CD-Rom.  That is the problem.  A USB stick is not a CD-Rom.   THIS is the bug in the install program that the programmers need to fix.  The install program ASSUMES that the install device MUST be a CD-Rom.

The solution to all these USB mounting problems, I believe,  is to simply comment out any line that starts out with  /dev/sbd1 ....  in it.

In fact, I guess you could delete it.  But the safe and cautious way would be to just comment out the line (or lines).  Add the pound sign in front of the line. like this:

#   /dev/sdb1       /mnt/USB        udf,iso9660 user,noauto,exec,utf8  0       0


My fully working Hardy 8.04 that I re-installed off of the CD-Rom (not installed off a USB stick) has ZERO references to  /dev/sdb1  in fstab.


I HATE this bug.  But this solved it for me.  Hardy behaves normally now.

I can mount and eject USB sticks all day long.  Problem solved.


same issue here after installation of hardy from a liveusb thumb drive : commenting out the offending fstab line did the trick

=D>

---

