---
title: "Xubuntu freezes with fan going crazy"
date: 2016-11-09
forum: General Help
---

### Post by bwuser on 2016-11-09
Hello,

my laptop with Xubuntu occasionally freezes. About one minute later the fan speeds up to maximum. CPU temperature is about 45°C to 48°C.

sudo dmidecode -t0 -t1:
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Acer
	Version: V1.03
	Release Date: 05/16/2014
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 4608 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 0.0
	Firmware Revision: 1.3


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Acer
	Product Name: Aspire E5-511
	Version: V1.03
	Serial Number: NXMNYEG005436154423400
	UUID: 5A0D2177-B631-E411-AA1F-F0761C290A39
	Wake-up Type: Power Switch
	SKU Number: Aspire E5-511_0905_V1.03
	Family: Bay Trail-M System

Unfortunately, there is no hint in the syslog:
1025 Nov  9 12:12:32 boris-laptop NetworkManager[759]: <info>  [1478689952.5858]   nameserver '134.96.7.100'
1026 Nov  9 12:12:32 boris-laptop NetworkManager[759]: <info>  [1478689952.5858]   nameserver '134.96.7.99'
1027 Nov  9 12:12:32 boris-laptop NetworkManager[759]: <info>  [1478689952.5859]   nameserver '134.96.7.5'
1028 Nov  9 12:12:32 boris-laptop NetworkManager[759]: <info>  [1478689952.5859]   domain name 'funklan.uni-saarland.de'
1029 Nov  9 12:12:32 boris-laptop NetworkManager[759]: <info>  [1478689952.5860] dhcp4 (wlan0): state changed bound -> bound
1030 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
1031 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
1032 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] Initializing cgroup subsys cpuacct
1033 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] Linux version 4.4.0-45-generic (buildd@lgw01-34) (gcc version 5.4.0 20160609      (Ubuntu 5.4.0-6ubuntu1~16.04.2) ) #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 (Ubuntu 4.4.0-45.66-generic 4.4.21)
1034 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-45-generic root=UUID=931a1e85-7a     c1-4dda-ae2f-7e50f86fcce7 ro no splash acpi_osi=Linux acpi_backlight=vendor quiet splash modprobe.blacklist=dw_dmac,dw_dmac_core      vt.handoff=7
1035 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] KERNEL supported cpus:
1036 Nov  9 12:17:49 boris-laptop kernel: [    0.000000]   Intel GenuineIntel
1037 Nov  9 12:17:49 boris-laptop kernel: [    0.000000]   AMD AuthenticAMD
1038 Nov  9 12:17:49 boris-laptop kernel: [    0.000000]   Centaur CentaurHauls
1039 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
1040 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
1041 Nov  9 12:17:49 boris-laptop kernel: [    0.000000] e820: BIOS-provided physical RAM map:

In the example log the freeze occured just before I restartet at 12:17.

The problem occurs since I use the 64-Bit version of Xubuntu. 

Does anyone have an idea how to find out what is the cause of this behaviour?

Thank you very much in adcance!

---

