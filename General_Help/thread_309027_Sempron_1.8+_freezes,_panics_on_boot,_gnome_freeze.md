---
title: "Sempron 1.8+ freezes, panics on boot, gnome freezes"
date: 2006-11-29
forum: General Help
---

### Post by Rene7705 on 2006-11-29
I'm running a Sempron 1800+ laptop, and just installed Ubuntu.

I'm a WinXP convert, and so far I like ubuntu (a lot), but I can't get it to run stable yet. :( 

Basically I get the following errors from time to time:

- on boot (esp when the laptop is 'cold' after a night of sleep), the kernel sometimes panics. Or it boots, but the startup screen goes blank instead of going to the login window. Takes about 5-7 retries to actually get it to boot.

- divx video playing sometimes freezes, restarting the player doesn't help; it plays about 5seconds - 1 minute, then freezes again.

- firefox sometimes freezes in such a way that xkill-ing and restarting it doesn't help either. a gnome-log-off and log-on doesnt help either in this case.

- gnome itself freezes sometimes.


Here's some info:

rene@falcon:~$ uname -a
Linux falcon 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Found a suspect too, but dont know how to correct this:
rene@falcon:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up linux-restricted-modules-2.6.15-26-386 (2.6.15.11-4) ...
/sbin/lrm-manager: line 85:  7307 Segmentation fault      depmod -a -q -F /boot/ System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-26-386
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anything you can tell me, on any of these subjects, is very much appreciated. Thank you for your brain-cycles ;)

---

### Post by drphilngood on 2006-11-29
enter:

```
df
```

in a terminal and post the results.

---

### Post by Rene7705 on 2006-11-29
rene@falcon:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda1             73939452   2370368  67813092   4% /
varrun                  517540        84    517456   1% /var/run
varlock                 517540         4    517536   1% /var/lock
udev                    517540       172    517368   1% /dev
devshm                  517540         0    517540   0% /dev/shm
lrm                     517540     18856    498684   4% /lib/modules/2.6.15-27-386/volatile
/dev/sda2              3904176   1366592   2537584  36% /media/ipod
tmpfs                   517540     18856    498684   4% /lib/modules/2.6.15-26-386/volatile



now why dont i like that /volatile bit? :)

---

### Post by drphilngood on 2006-11-29
Volatile doesn´t mean what you think it does.;)

I´d like to see the following logs.

/var/log/Xorg.0.log

/var/log/syslog

/var/log/kern.log

Do you know how to post attachments?

---

### Post by Rene7705 on 2006-11-29
Sure, no problem :)

---

### Post by drphilngood on 2006-11-29
I have found others(in [this thread]("http://ubuntuforums.org/showthread.php?t=258177"), for instance) with problems like yours that appear to be caused by the update to the 2.6.15-26-386 kernel.  Many of them decided to install Ubuntu 6.10, because of this, while others suggest installing the 686 or k7 kernel.  Therefore, I suggest we try installing the k7 kernel, since you have a sempron and it will also give you a performance boost.

From the information you shared with me, it seems that you don´t have anything nVidia(if I´m mistaken, stop now and post back).  If this is so, just enter the following in a terminal:
```
sudo apt-get update
```
and then
```
sudo apt-get install linux-k7
```

then reboot.  

Apt-get should have installed everything you need but if not and you are stuck to the command line type:

```
sudo dpkg-reconfigure xserver-xorg
```

and just answer yes/hit enter, for anything you don´t know.

If you want to revert to the old kernel, hit escape as the computer is booting and select it in Grub.

[This thread]("http://ubuntuforums.org/showthread.php?t=85917") pertains to installing a new kernel if you´d like to read it.

Finally, I´m no expert.  I´m just telling you what I would do if in your situation.  Therefore, you may want to seek verification from the forum elders.

Good luck!

---

### Post by Rene7705 on 2006-11-30
A more specific kernel might be the trick, i hope so :)


Here's the log;

rene@falcon:~$ sudo apt-get install linux-k7
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-image-2.6.15-27-k7 linux-image-k7 linux-restricted-modules-2.6.15-27-k7 linux-restricted-modules-k7
Suggested packages:
  linux-doc-2.6.15 linux-source-2.6.15 nvidia-glx nvidia-glx-legacy avm-fritz-firmware-2.6.15-27
Recommended packages:
  lilo
The following NEW packages will be installed:
  linux-image-2.6.15-27-k7 linux-image-k7 linux-k7 linux-restricted-modules-2.6.15-27-k7 linux-restricted-modules-k7
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 30.2MB of archives.
After unpacking 86.6MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-27-k7 2.6.15-27.48 [22.2MB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-k7 2.6.15.25 [23.4kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-2.6.15-27-k7 2.6.15.12-1 [7939kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-k7 2.6.15.25 [23.4kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-k7 2.6.15.25 [23.4kB]
Fetched 30.2MB in 1m5s (461kB/s)
Selecting previously deselected package linux-image-2.6.15-27-k7.
(Reading database ... 77774 files and directories currently installed.)
Unpacking linux-image-2.6.15-27-k7 (from .../linux-image-2.6.15-27-k7_2.6.15-27.48_i386.deb) ...
Selecting previously deselected package linux-image-k7.
Unpacking linux-image-k7 (from .../linux-image-k7_2.6.15.25_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.15-27-k7.
Unpacking linux-restricted-modules-2.6.15-27-k7 (from .../linux-restricted-modules-2.6.15-27-k7_2.6.15.12-1_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-k7.
Unpacking linux-restricted-modules-k7 (from .../linux-restricted-modules-k7_2.6.15.25_i386.deb) ...
Selecting previously deselected package linux-k7.
Unpacking linux-k7 (from .../linux-k7_2.6.15.25_i386.deb) ...
Setting up linux-restricted-modules-2.6.15-26-386 (2.6.15.11-4) ...
/sbin/lrm-manager: line 85: 16745 Segmentation fault      depmod -a -q -F /boot/System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up linux-image-2.6.15-27-k7 (2.6.15-27.48) ...
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-27-k7
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-image-k7 (2.6.15.25) ...
Setting up linux-restricted-modules-2.6.15-27-k7 (2.6.15.12-1) ...

Setting up linux-restricted-modules-k7 (2.6.15.25) ...
Setting up linux-k7 (2.6.15.25) ...
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-26-386
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm rebooting now. Hope my machine aint criplled <g>

---

### Post by Rene7705 on 2006-11-30
[17179569.184000] Linux version 2.6.15-27-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006


Looking good <G>

I'll post in a few days how i fare with this kernel.

drphlngood, thanks for the help :)

---

### Post by Rene7705 on 2006-11-30
The first total freeze (not even ctrl-alt-f1-ing anymore) happened within 10 minutes of boot :(

Could be this nagging:

rene@falcon:~$ sudo apt-get remove linux-restricted-modules-2.6.15-26-386
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
rene@falcon:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
rene@falcon:~$ sudo dpkg --configure -a
Setting up linux-restricted-modules-2.6.15-26-386 (2.6.15.11-4) ...
/sbin/lrm-manager: line 85:  5329 Segmentation fault      depmod -a -q -F /boot/ System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-26-386
rene@falcon:~$ sudo apt-get remove linux-restricted-modules-2.6.15-26-386
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.15-26-386
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 22.1MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 81753 files and directories currently installed.)
Removing linux-restricted-modules-2.6.15-26-386 ...
/var/lib/dpkg/info/linux-restricted-modules-2.6.15-26-386.postrm: line 10:  5348  Segmentation fault      depmod -a -q -F /boot/System.map-2.6.15-26-386 2.6.15-2 6-386

Also:
rene@falcon:~$ dpkg -l | grep restricted
rc  linux-restricted-modules-2.6.15-26-386 2.6.15.11-4                             Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-27-386 2.6.15.12-1                             Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-27-k7  2.6.15.12-1                             Non-free Linux 2.6.15 modules on AMD K7
ii  linux-restricted-modules-386           2.6.15.25                               Restricted Linux modules on 386.
ii  linux-restricted-modules-common        2.6.15.12-1                             Non-free Linux 2.6.15 modules helper script
ii  linux-restricted-modules-k7            2.6.15.25                               Restricted Linux modules on AMD K7.

So ehm... how do i get rid of the buggy excess code?

---

### Post by Rene7705 on 2006-11-30
Aargh. My average uptime is now less than 5 minutes.
I need some more tips dear ppl :)

btw; i already removed linux-k7. didnt help.

---

### Post by drphilngood on 2006-11-30
What do you get when you enter:

```
dmesg
```

in a terminal?

and let´s have a look at your repos:

```
gedit /etc/apt/sources.list
```

---

### Post by Rene7705 on 2006-11-30
Ok, in order to simplify things (hopefully), i did a re-install followed by

apt-get update
apt-get install linux-k7
apt-get upgrade

rene@falcon:~$  cat /etc/apt/sources.list

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



It still freezes (quickly after boot), but can retrieve the dmesg:

rene@falcon:~$ sudo dmesg
Password:
[17179569.184000] Linux version 2.6.15-27-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fef0000 - 000000003fefa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fefa000 - 000000003ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6850
[17179569.184000] On node 0 totalpages: 261872
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32496 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f68d0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x3fef619a
[17179569.184000] ACPI: FADT (v001 AMDK8  PTLTW    0x06040000 PTL_ 0x000f4240) @ 0x3fef9e41
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x3fef9eb5
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x3fef9f8b
[17179569.184000] ACPI: OEMT (v001 PTLTD  OEMTTBL  0x06040000  LTP 0x00000001) @ 0x3fef9fdb
[17179569.184000] ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ10 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffe0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 801.956 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.516000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.516000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.560000] Memory: 1026200k/1047488k available (2103k kernel code, 20560k reserved, 599k data, 332k init, 129984k highmem)
[17179571.560000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.640000] Calibrating delay using timer specific routine.. 1606.33 BogoMIPS (lpj=3212662)
[17179571.640000] Security Framework v1.0.0 initialized
[17179571.640000] SELinux:  Disabled at boot.
[17179571.640000] Mount-cache hash table entries: 512
[17179571.640000] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.640000] CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.640000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.640000] CPU: L2 Cache: 128K (64 bytes/line)
[17179571.640000] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179571.640000] mtrr: v2.0 (20020519)
[17179571.640000] Enabling fast FPU save and restore... done.
[17179571.640000] Enabling unmasked SIMD FPU exception support... done.
[17179571.640000] Checking 'hlt' instruction... OK.
[17179571.656000] SMP alternatives: switching to UP code
[17179571.656000] checking if image is initramfs... it is
[17179572.900000] Freeing initrd memory: 6763k freed
[17179572.908000] ACPI: Looking for DSDT ... not found!
[17179572.916000] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[17179572.916000] Total of 1 processors activated (1606.33 BogoMIPS).
[17179572.916000] ENABLING IO-APIC IRQs
[17179572.916000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.060000] Brought up 1 CPUs
[17179573.060000] NET: Registered protocol family 16
[17179573.060000] EISA bus registered
[17179573.060000] ACPI: bus type pci registered
[17179573.064000] PCI: PCI BIOS revision 2.10 entry at 0xfd8dc, last bus=1
[17179573.064000] PCI: Using configuration type 1
[17179573.064000] ACPI: Subsystem revision 20051216
[17179573.068000] ACPI: Interpreter enabled
[17179573.068000] ACPI: Using IOAPIC for interrupt routing
[17179573.072000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.072000] PCI: Probing PCI hardware (bus 00)
[17179573.076000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179573.076000] PCI quirk: region 8100-810f claimed by vt8235 SMB
[17179573.076000] Boot video device is 0000:01:00.0
[17179573.076000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.088000] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[17179573.088000] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *11, disabled.
[17179573.092000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *10, disabled.
[17179573.092000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *5, disabled.
[17179573.092000] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[17179573.092000] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[17179573.092000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[17179573.092000] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[17179573.096000] ACPI: Embedded Controller [EC] (gpe 11) interrupt mode.
[17179573.204000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.204000] pnp: PnP ACPI init
[17179573.260000] pnp: PnP ACPI: found 11 devices
[17179573.260000] PnPBIOS: Disabled by ACPI PNP
[17179573.260000] PCI: Using ACPI for IRQ routing
[17179573.260000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.264000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
[17179573.264000] pnp: 00:05: ioport range 0xe680-0xe6ed has been reserved
[17179573.264000] pnp: 00:05: ioport range 0xe6f2-0xe6f7 has been reserved
[17179573.264000] pnp: 00:05: ioport range 0xfe10-0xfe11 could not be reserved
[17179573.264000] PCI: Bridge: 0000:00:01.0
[17179573.264000]   IO window: 2000-2fff
[17179573.264000]   MEM window: d0100000-d01fffff
[17179573.264000]   PREFETCH window: d8000000-dfffffff
[17179573.264000] PCI: Bus 2, cardbus bridge: 0000:00:0c.0
[17179573.264000]   IO window: 00003000-000030ff
[17179573.264000]   IO window: 00003400-000034ff
[17179573.264000]   PREFETCH window: 50000000-51ffffff
[17179573.264000]   MEM window: 52000000-53ffffff
[17179573.264000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.264000] PCI: Enabling device 0000:00:0c.0 (0000 -> 0003)
[17179573.264000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.264000] audit: initializing netlink socket (disabled)
[17179573.268000] audit(1164880678.264:1): initialized
[17179573.268000] highmem bounce pool size: 64 pages
[17179573.268000] VFS: Disk quotas dquot_6.5.1
[17179573.268000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.268000] Initializing Cryptographic API
[17179573.268000] io scheduler noop registered
[17179573.268000] io scheduler anticipatory registered
[17179573.268000] io scheduler deadline registered
[17179573.268000] io scheduler cfq registered
[17179573.268000] isapnp: Scanning for PnP cards...
[17179573.624000] isapnp: No Plug & Play device found
[17179573.648000] Real Time Clock Driver v1.12
[17179573.648000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.652000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.652000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.652000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.652000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.652000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.652000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.652000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.652000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.656000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.660000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.660000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.660000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.660000] mice: PS/2 mouse device common for all mice
[17179573.660000] EISA: Probing bus 0 at eisa.0
[17179573.660000] Cannot allocate resource for EISA slot 1
[17179573.660000] Cannot allocate resource for EISA slot 2
[17179573.660000] Cannot allocate resource for EISA slot 3
[17179573.660000] Cannot allocate resource for EISA slot 4
[17179573.660000] EISA: Detected 0 cards.
[17179573.660000] NET: Registered protocol family 2
[17179573.700000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.700000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[17179573.700000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179573.704000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.704000] TCP reno registered
[17179573.704000] TCP bic registered
[17179573.704000] NET: Registered protocol family 1
[17179573.704000] NET: Registered protocol family 8
[17179573.704000] NET: Registered protocol family 20
[17179573.704000] Using IPI No-Shortcut mode
[17179573.704000] ACPI wakeup devices:
[17179573.704000] PCI0 MD97 USB1 USB2 USB3 USB4 SLPB  LID
[17179573.704000] ACPI: (supports S0 S3 S4 S5)
[17179573.704000] Freeing unused kernel memory: 332k freed
[17179573.816000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.820000] vga16fb: initializing
[17179573.820000] vga16fb: mapped to 0xc00a0000
[17179573.948000] Console: switching to colour frame buffer device 80x25
[17179573.948000] fb0: VGA16 VGA frame buffer device
[17179575.116000] Capability LSM initialized
[17179575.204000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.568000] ACPI: Thermal Zone [THRM] (25 C)
[17179576.892000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.892000] **** SET: Misaligned resource pointer: df871d02 Type 07 Len 0
[17179576.892000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug.
[17179576.892000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
[17179576.892000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
[17179576.892000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 23 (level, low) -> IRQ 177
[17179576.892000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179576.892000] VP_IDE: chipset revision 6
[17179576.892000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.892000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179576.892000]     ide0: BM-DMA at 0x1c60-0x1c67, BIOS settings: hda:DMA, hdb:pio
[17179576.892000]     ide1: BM-DMA at 0x1c68-0x1c6f, BIOS settings: hdc:DMA, hdd:pio
[17179576.892000] Probing IDE interface ide0...
[17179577.312000] hda: HITACHI_DK23FA-80, ATA DISK drive
[17179577.984000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.988000] Probing IDE interface ide1...
[17179578.852000] hdc: MATSHITADVD-RAM UJ-815A, ATAPI CD/DVD-ROM drive
[17179579.188000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.204000] hda: max request size: 128KiB
[17179579.220000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179579.220000] hda: cache flushes supported
[17179579.220000]  hda: hda1 hda2 < hda5 >
[17179579.280000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.280000] Uniform CD-ROM driver Revision: 3.20
[17179579.576000] ieee1394: Initialized config rom entry `ip1394'
[17179579.612000] usbcore: registered new driver usbfs
[17179579.616000] usbcore: registered new driver hub
[17179579.620000] USB Universal Host Controller Interface driver v2.3
[17179579.620000] **** SET: Misaligned resource pointer: df871882 Type 07 Len 0
[17179579.620000] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug.
[17179579.620000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[17179579.620000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[17179579.620000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 185
[17179579.620000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 9
[17179579.620000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179579.624000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179579.624000] uhci_hcd 0000:00:10.0: irq 185, io base 0x00001c00
[17179579.628000] hub 1-0:1.0: USB hub found
[17179579.628000] hub 1-0:1.0: 2 ports detected
[17179579.732000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 185
[17179579.732000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 9
[17179579.732000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179579.732000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179579.732000] uhci_hcd 0000:00:10.1: irq 185, io base 0x00001c20
[17179579.732000] hub 2-0:1.0: USB hub found
[17179579.732000] hub 2-0:1.0: 2 ports detected
[17179579.736000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179579.736000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179579.784000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[d0008000-d00087ff]  Max Packet=[2048]
[17179579.836000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 185
[17179579.836000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 9
[17179579.836000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179579.836000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179579.836000] uhci_hcd 0000:00:10.2: irq 185, io base 0x00001c40
[17179579.836000] hub 3-0:1.0: USB hub found
[17179579.836000] hub 3-0:1.0: 2 ports detected
[17179579.944000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 185
[17179579.944000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 9
[17179579.944000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179579.944000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179579.944000] ehci_hcd 0000:00:10.3: irq 185, io mem 0xd0008c00
[17179579.944000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.944000] hub 4-0:1.0: USB hub found
[17179579.944000] hub 4-0:1.0: 6 ports detected
[17179579.972000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179580.144000] Attempting manual resume
[17179580.188000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.224000] kjournald starting.  Commit interval 5 seconds
[17179581.056000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090f50000326fdf]
[17179581.284000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[17179581.696000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17179581.836000] hub 1-2:1.0: USB hub found
[17179581.840000] hub 1-2:1.0: 4 ports detected
[17179582.152000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[17179593.088000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.092000] agpgart: Detected AGP bridge 0
[17179593.412000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.564000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179593.564000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.564000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179593.564000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179593.564000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179593.564000] eth0: RTL8169 at 0xf89aa800, 00:90:f5:32:6f:df, IRQ 201
[17179594.096000] ieee80211_crypt: registered algorithm 'NULL'
[17179594.108000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179594.108000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179594.132000] irda_init()
[17179594.132000] NET: Registered protocol family 23
[17179594.360000] Loaded islsm_pci driver, version 0
[17179594.360000] PCI: Enabling device 0000:00:05.0 (0000 -> 0002)
[17179594.360000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.944000] **** SET: Misaligned resource pointer: dfa813c2 Type 07 Len 0
[17179594.944000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug.
[17179594.944000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179594.944000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179594.944000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
[17179594.944000] PCI: Via IRQ fixup for 0000:00:11.6, from 10 to 1
[17179594.948000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179595.016000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179595.016000] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:4701]
[17179595.016000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179595.016000] Yenta: Routing CardBus interrupts to PCI
[17179595.016000] Yenta TI: socket 0000:00:0c.0, mfunc 0x00001002, devctl 0x44
[17179595.248000] Yenta: ISA IRQ mask 0x0a40, PCI irq 169
[17179595.248000] Socket status: 30000006
[17179595.368000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
[17179595.368000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 1
[17179595.368000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179595.376000] input: PS/2 Mouse as /class/input/input1
[17179595.392000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[17179595.520000] usbcore: registered new driver hiddev
[17179595.536000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[17179595.536000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1
[17179595.536000] usbcore: registered new driver usbhid
[17179595.536000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179596.020000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2911
[17179596.020000] usbcore: registered new driver usblp
[17179596.020000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179596.120000] SCSI subsystem initialized
[17179596.156000] Initializing USB Mass Storage driver...
[17179596.156000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179596.156000] usb-storage: device found at 5
[17179596.156000] usb-storage: waiting for device to settle before scanning
[17179596.156000] usbcore: registered new driver usb-storage
[17179596.156000] USB Mass Storage support registered.
[17179596.340000] input: PC Speaker as /class/input/input4
[17179596.480000] parport: PnPBIOS parport detected.
[17179596.480000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179596.800000] r8169: eth0: link up
[17179597.000000] ts: Compaq touchscreen protocol output
[17179597.304000] cs: IO port probe 0x100-0x3af: clean.
[17179597.308000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179597.308000] cs: IO port probe 0x820-0x8ff: clean.
[17179597.312000] cs: IO port probe 0xc00-0xcf7: clean.
[17179597.312000] cs: IO port probe 0xa00-0xaff: clean.
[17179598.544000] lp0: using parport0 (interrupt-driven).
[17179598.596000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179598.596000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179598.596000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179598.720000] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[17179598.856000] NET: Registered protocol family 17
[17179598.952000] EXT3 FS on hda1, internal journal
[17179599.228000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179599.228000] md: bitmap version 4.39
[17179600.160000] NET: Registered protocol family 10
[17179600.160000] lo: Disabled Privacy Extensions
[17179600.160000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[17179600.160000] IPv6 over IPv4 tunneling driver
[17179600.616000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179601.176000]   Vendor: HP        Model: psc 2210          Rev: 1.00
[17179601.176000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179601.180000] usb-storage: device scan complete
[17179601.272000] Driver 'sd' needs updating - please use bus_type methods
[17179601.288000] sd 0:0:0:0: Attached scsi removable disk sda
[17179601.308000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179601.536000] cdrom: open failed.
[17179607.764000] ACPI: AC Adapter [AC] (on-line)
[17179609.224000] ACPI: Battery Slot [BAT0] (battery present)
[17179609.380000] ACPI: Power Button (FF) [PWRF]
[17179609.380000] ACPI: Power Button (CM) [PWB]
[17179609.380000] ACPI: Sleep Button (CM) [SLPB]
[17179609.380000] ACPI: Lid Switch [LID]
[17179609.628000] ibm_acpi: ec object not found
[17179609.680000] pcc_acpi: loading...
[17179610.540000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179610.540000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[17179610.540000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa (1300 mV)
[17179610.540000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[17179610.540000] cpu_init done, current fid 0x0, vid 0x4
[17179611.052000] eth0: no IPv6 routers present
[17179614.240000] [drm] Initialized drm 1.0.1 20051102
[17179614.268000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179614.268000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179615.004000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179615.004000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179615.004000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179615.136000] ppdev: user-space parallel port driver
[17179615.420000] [drm] Setting GART location based on new memory map
[17179615.420000] [drm] Loading R300 Microcode
[17179615.420000] [drm] writeback test succeeded in 1 usecs
[17179615.512000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179615.512000] apm: overridden by ACPI.
[17179623.088000] Bluetooth: Core ver 2.8
[17179623.088000] NET: Registered protocol family 31
[17179623.088000] Bluetooth: HCI device and connection manager initialized
[17179623.088000] Bluetooth: HCI socket layer initialized
[17179623.108000] Bluetooth: L2CAP ver 2.8
[17179623.108000] Bluetooth: L2CAP socket layer initialized
[17179623.112000] Bluetooth: RFCOMM socket layer initialized
[17179623.112000] Bluetooth: RFCOMM TTY layer initialized
[17179623.112000] Bluetooth: RFCOMM ver 1.7

---

### Post by drphilngood on 2006-11-30
Did this notebook run without problems prior to installing Ubuntu?  Does it function properly when running from the Live CD(if you have one)?  Which version of the installation CD did you use when installing?

What is the exact name-make-model of this notebook?  Does it run hot?  Have you tested the ram?

---

### Post by Rene7705 on 2006-11-30
> **drphilngood said:**
> Did this notebook run without problems prior to installing Ubuntu?  Does it function properly when running from the Live CD(if you have one)?  Which version of the installation CD did you use when installing?

What is the exact name-make-model of this notebook?  Does it run hot?  Have you tested the ram?
When I ran winXP, i had problems with the (latest) AMD cpu-scaling driver, that caused crashes too.
The model is a Cybermaxx MD95129, with a Clevo D470K motherboard and a Sempron 0.8-1.8 cpu
I haven't explicitly tested the RAM, i dont know how ;)

The Live CD of ubuntu works much like a linux-386 system; it sometimes freezes firefox, but not gnome itself..
The CD i'm using comes from [ftp://ftpserv.tudelft.nl/pub/Linux/releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso](ftp://ftpserv.tudelft.nl/pub/Linux/releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso)

---

### Post by Rene7705 on 2006-11-30
And it doesnt run very hot, it also crashed without the cpu-fans activated, possibly indicating it was in cpu powersave mode..

---

### Post by Rene7705 on 2006-11-30
I just noticed the nifty memtest86+ in grub ;)
I'll post the results when it's done, seems to need plenty of time..

---

### Post by drphilngood on 2006-11-30
> **Rene7705 said:**
> I just noticed the nifty memtest86+ in grub ;)
I'll post the results when it's done, seems to need plenty of time..

Here´s the [manual]("http://hcidesign.com/memtest/manual.html") for any questions you might have about memtest.

---

### Post by Rene7705 on 2006-11-30
I'm now running -386 again, which doesn't instantly total-freeze..

The memtest86+ ran for 58 minutes or so, did all it's tests, and had 0 errors.

I'm looking for a way to disable cpu frequency scaling alltogether to see if that might help.

---

### Post by drphilngood on 2006-11-30
> **Rene7705 said:**
> I'm now running -386 again, which doesn't instantly total-freeze..

The memtest86+ ran for 58 minutes or so, did all it's tests, and had 0 errors.

I'm looking for a way to disable cpu frequency scaling alltogether to see if that might help.

See here:
[URL="http://quotedprintable.com/articles/2005/11/24/enabling-cpu-frequency-scaling-in-ubuntu"]
Enable CPU frequency scaling in Ubuntu[/URL]

edit:
It is recommended to allow memtest to run overnight(8 hours) at least.

---

### Post by Rene7705 on 2006-11-30
Ok, i'll run memtest again tonight..

I've also root-suid the frequency panel and am now running on 0.8-fixed.
Hope it helps, and i'll let you know..

Thanks again for the help so far ;)

---

### Post by drphilngood on 2006-11-30
> **Rene7705 said:**
> Ok, i'll run memtest again tonight..

I've also root-suid the frequency panel and am now running on 0.8-fixed.
Hope it helps, and i'll let you know..

Thanks again for the help so far ;)

You are most welcome.  Eventually, we´ll get it all sorted.:)

---

### Post by Rene7705 on 2006-12-01
Well, memtest86 ran 13 complete passes in 13.5 hours, had 12 errors in step 5 of pass 0, but none after that.

Hope this means memtest  was a bit too paranoid?

Still running linux-386 on 0.8Ghz nonscaled, but it too freezes processes.
Sometimes the video playback (which a player restart doesnt fix), sometimes firefox. ps aux | grep Z doesnt show any zombies when it does..

---

### Post by Bremen Saki on 2006-12-01
This all sounds almost exactly like what's going on with my Sempron 2800 desktop machine. Random complete lockups. I'm still digging into it, and if I find anything interesting in the logs, I'll post.

Installed from the 6.10 desktop-amd64 LiveCD which ran fine - nothing suspicious during that stage. First lockups started after installing a few packages. It seems that installing samba will reliably cause a hang, so I'll start there.

This machine is rock-solid on Fedora Core 6 (where I do most of my work right now) and Windows XP. I have no reason to suspect the hardware at all.

---

### Post by Rene7705 on 2006-12-01
I still haven't upgraded this -386 kernel from the ubuntu-6.06.1-desktop-386.iso install either, and has run the enitre day without freezing, while i did edit a website with gimp, vim, ssh, ftp and firefox.

The update manager (next to clock on top-right of desktop) wants to install: 
evince    v 0.5.2-0ubuntu3.1
linux-image-2.6.15-48
linux-image-386   v 2.6.15.25
linux-restricted-modules-2.16.15-27-386
linux-restricted-modules-386
lvm2    v 2.02.02-1ubuntu1.2

It was the restricted modules I had problems with earlier.
Lets just say i really hope that skipping the upgrades will keep my sys stable.

---

### Post by drphilngood on 2006-12-02
> **Rene7705 said:**
> I still haven't upgraded this -386 kernel from the ubuntu-6.06.1-desktop-386.iso install either, and has run the enitre day without freezing, while i did edit a website with gimp, vim, ssh, ftp and firefox.

The update manager (next to clock on top-right of desktop) wants to install: 
evince    v 0.5.2-0ubuntu3.1
linux-image-2.6.15-48
linux-image-386   v 2.6.15.25
linux-restricted-modules-2.16.15-27-386
linux-restricted-modules-386
lvm2    v 2.02.02-1ubuntu1.2

It was the restricted modules I had problems with earlier.
Lets just say i really hope that skipping the upgrades will keep my sys stable.

Maybe just installing security updates is a good idea.

---

### Post by Rene7705 on 2006-12-03
update: i haven't had any problems since running ubuntu-6.06.1-desktop-386.iso and **not** updating with the updates 

linux-image-2.6.15-48
linux-image-386 v 2.6.15.25
linux-restricted-modules-2.16.15-27-386
linux-restricted-modules-386

I've installed a bunch of gadgets, java, etc. No freezes or crashes.
Think i'm outta the woods ;)

---

### Post by drphilngood on 2006-12-04
> **Rene7705 said:**
> update: i haven't had any problems since running ubuntu-6.06.1-desktop-386.iso and **not** updating with the updates 

linux-image-2.6.15-48
linux-image-386 v 2.6.15.25
linux-restricted-modules-2.16.15-27-386
linux-restricted-modules-386

I've installed a bunch of gadgets, java, etc. No freezes or crashes.
Think i'm outta the woods ;)

Good to see things are going well, Rene7705!  Hopefully, it´ll be smooth sailing for you, from now on.

Take care, my friend.

---

### Post by Rene7705 on 2006-12-06
When I installed a few more gadgets like wine and IE6, i started running into bugs again..

Dec  6 09:20:16 falcon kernel: [17179786.692000] kernel BUG at mm/rmap.c:486!
Dec  6 09:20:16 falcon kernel: [17179786.692000] invalid operand: 0000 [#1]
Dec  6 09:20:16 falcon kernel: [17179786.692000] PREEMPT

---

### Post by Rene7705 on 2006-12-06
Trying to install 2.6.19 kernel to see if that fixes the rmap issue, but then i run into this:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[ftp://kernel.org/pub/linux/kernel/linux-2.6.19.tar.gz](ftp://kernel.org/pub/linux/kernel/linux-2.6.19.tar.gz)

root@falcon:/usr/src/linux# fakeroot make-kpkg --initrd --append-to-version=-bleed kernel_image kernel_headers
....
  CC      kernel/exit.o
In file included from kernel/exit.c:9:
include/linux/interrupt.h: In function ‘disable_irq_nosync_lockdep_irqsave’:
include/linux/interrupt.h:133: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [kernel/exit.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [stamp-build] Error 2

---

### Post by Rene7705 on 2006-12-06
As with windows, re-installing helps.

Wish operating systems had decent self-diagnostics..

---

### Post by drphilngood on 2006-12-09
I am starting to suspect that you are using some bad repos or the wrong repos.

---

