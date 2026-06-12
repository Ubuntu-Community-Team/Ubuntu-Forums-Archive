---
title: "Ubuntu 16.04 - systemd[1]: freezing execution"
date: 2021-01-08
forum: General Help
---

### Post by alessandro4891 on 2021-01-08
Hi to all, I'm not an expert linux user but some years ago (reading many tutorials) I decided to create my own NAS on a Ubuntu 16.04 LTS with a 4Tb in RAID1.
I had no problem till now but today when I started the machine I eard a BIIIP noise.
The problem was on the battery so I changed it an re-set the date on the BIOS.
Now when I'm trying to read or copy files from the RAID partition to other PCs connected on the LAN I receive some errors (attached at the end) :

systemd[1]: freezing execution
or 
segmentation fault

and the machine doesn't respond.
I'm a little afraid because I have a lot of data in the RAID partition and I wan't to lost it all.
(I'm also not able to restore or recover data if some Disk is corrupt; I never ever did it before)
Is there some check that can I do to understand the problem?

I add some information about my system:[INDENT=3]
[/INDENT]
[INDENT=3]ubuntu[/INDENT]
[INDENT=3]    description: Computer[/INDENT]
[INDENT=3]    width: 64 bits[/INDENT]
[INDENT=3]    capabilities: smbios-2.5 vsyscall32[/INDENT]
[INDENT=3]  *-core[/INDENT]
[INDENT=3]       description: Motherboard[/INDENT]
[INDENT=3]       physical id: 0[/INDENT]
[INDENT=3]     *-memory[/INDENT]
[INDENT=3]          description: System memory[/INDENT]
[INDENT=3]          physical id: 0[/INDENT]
[INDENT=3]          size: 7903MiB[/INDENT]
[INDENT=3]     *-cpu[/INDENT]
[INDENT=3]          product: Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz[/INDENT]
[INDENT=3]          vendor: Intel Corp.[/INDENT]
[INDENT=3]          physical id: 1[/INDENT]
[INDENT=3]          bus info: cpu@0[/INDENT]
[INDENT=3]          size: 1998MHz[/INDENT]
[INDENT=3]          capacity: 2833MHz[/INDENT]
[INDENT=3]          width: 64 bits[/INDENT]
[INDENT=3]          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm kaiser tpr_shadow vnmi flexpriority dtherm cpufreq[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]        *-network[/INDENT]
[INDENT=3]             description: Ethernet interface[/INDENT]
[INDENT=3]             product: 82566DM-2 Gigabit Network Connection[/INDENT]
[INDENT=3]             vendor: Intel Corporation[/INDENT]
[INDENT=3]             physical id: 19[/INDENT]
[INDENT=3]             bus info: pci@0000:00:19.0[/INDENT]
[INDENT=3]             logical name: enp0s25[/INDENT]
[INDENT=3]             version: 02[/INDENT]
[INDENT=3]             serial: 00:0f:fe:d3:0e:a6[/INDENT]
[INDENT=3]             size: 100Mbit/s[/INDENT]
[INDENT=3]             capacity: 1Gbit/s[/INDENT]
[INDENT=3]             width: 32 bits[/INDENT]
[INDENT=3]             clock: 33MHz[/INDENT]
[INDENT=3]             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/INDENT]
[INDENT=3]             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=1.3-1 ip=192.168.1.20 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/INDENT]
[INDENT=3]             resources: irq:26 memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]     *-scsi:0[/INDENT]
[INDENT=3]          physical id: 2[/INDENT]
[INDENT=3]          logical name: scsi0[/INDENT]
[INDENT=3]          capabilities: emulated[/INDENT]
[INDENT=3]        *-disk[/INDENT]
[INDENT=3]             description: ATA Disk[/INDENT]
[INDENT=3]             product: ST3250620AS[/INDENT]
[INDENT=3]             vendor: Seagate[/INDENT]
[INDENT=3]             physical id: 0.0.0[/INDENT]
[INDENT=3]             bus info: scsi@0:0.0.0[/INDENT]
[INDENT=3]             logical name: /dev/sda[/INDENT]
[INDENT=3]             version: D[/INDENT]
[INDENT=3]             serial: 3QE07LVJ[/INDENT]
[INDENT=3]             size: 232GiB (250GB)[/INDENT]
[INDENT=3]             capabilities: partitioned partitioned:dos[/INDENT]
[INDENT=3]             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=9d1fad8f[/INDENT]
[INDENT=3]           *-volume:0[/INDENT]
[INDENT=3]                description: EXT4 volume[/INDENT]
[INDENT=3]                vendor: Linux[/INDENT]
[INDENT=3]                physical id: 1[/INDENT]
[INDENT=3]                bus info: scsi@0:0.0.0,1[/INDENT]
[INDENT=3]                logical name: /dev/sda1[/INDENT]
[INDENT=3]                logical name: /[/INDENT]
[INDENT=3]                version: 1.0[/INDENT]
[INDENT=3]                serial: a633cdd9-3ffb-48d8-b9dd-c1381bb45e25[/INDENT]
[INDENT=3]                size: 224GiB[/INDENT]
[INDENT=3]                capacity: 224GiB[/INDENT]
[INDENT=3]                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized[/INDENT]
[INDENT=3]                configuration: created=2016-07-14 17:53:19 filesystem=ext4 lastmountpoint=/ modified=2021-01-08 18:17:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2021-01-08 18:02:43 state=mounted[/INDENT]
[INDENT=3]           *-volume:1[/INDENT]
[INDENT=3]                description: Extended partition[/INDENT]
[INDENT=3]                physical id: 2[/INDENT]
[INDENT=3]                bus info: scsi@0:0.0.0,2[/INDENT]
[INDENT=3]                logical name: /dev/sda2[/INDENT]
[INDENT=3]                size: 8110MiB[/INDENT]
[INDENT=3]                capacity: 8110MiB[/INDENT]
[INDENT=3]                capabilities: primary extended partitioned partitioned:extended[/INDENT]
[INDENT=3]              *-logicalvolume[/INDENT]
[INDENT=3]                   description: Linux swap / Solaris partition[/INDENT]
[INDENT=3]                   physical id: 5[/INDENT]
[INDENT=3]                   logical name: /dev/sda5[/INDENT]
[INDENT=3]                   capacity: 8110MiB[/INDENT]
[INDENT=3]                   capabilities: nofs[/INDENT]
[INDENT=3]    *-scsi:1[/INDENT]
[INDENT=3]          physical id: 3[/INDENT]
[INDENT=3]          logical name: scsi1[/INDENT]
[INDENT=3]          capabilities: emulated[/INDENT]
[INDENT=3]        *-disk[/INDENT]
[INDENT=3]             description: ATA Disk[/INDENT]
[INDENT=3]             product: TOSHIBA MD04ACA4[/INDENT]
[INDENT=3]             vendor: Toshiba[/INDENT]
[INDENT=3]             physical id: 0.0.0[/INDENT]
[INDENT=3]             bus info: scsi@1:0.0.0[/INDENT]
[INDENT=3]             logical name: /dev/sdb[/INDENT]
[INDENT=3]             version: FP2A[/INDENT]
[INDENT=3]             serial: Z5F9KEYNFSAA[/INDENT]
[INDENT=3]             size: 3726GiB (4TB)[/INDENT]
[INDENT=3]             capabilities: gpt-1.00 partitioned partitioned:gpt[/INDENT]
[INDENT=3]             configuration: ansiversion=5 guid=807cfe1b-ec4b-45cb-8896-6a0b33e18dd4 logicalsectorsize=512 sectorsize=4096[/INDENT]
[INDENT=3]           *-volume[/INDENT]
[INDENT=3]                description: EFI partition[/INDENT]
[INDENT=3]                physical id: 1[/INDENT]
[INDENT=3]                bus info: scsi@1:0.0.0,1[/INDENT]
[INDENT=3]                logical name: /dev/sdb1[/INDENT]
[INDENT=3]                serial: 279d1941-fb29-41b5-84d8-ffe8f0b2aea9[/INDENT]
[INDENT=3]                capacity: 3726GiB[/INDENT]
[INDENT=3]     *-scsi:2[/INDENT]
[INDENT=3]          physical id: 4[/INDENT]
[INDENT=3]          logical name: scsi2[/INDENT]
[INDENT=3]          capabilities: emulated[/INDENT]
[INDENT=3]        *-disk[/INDENT]
[INDENT=3]             description: ATA Disk[/INDENT]
[INDENT=3]             product: TOSHIBA MD04ACA4[/INDENT]
[INDENT=3]             vendor: Toshiba[/INDENT]
[INDENT=3]             physical id: 0.0.0[/INDENT]
[INDENT=3]             bus info: scsi@2:0.0.0[/INDENT]
[INDENT=3]             logical name: /dev/sdc[/INDENT]
[INDENT=3]             version: FP2A[/INDENT]
[INDENT=3]             serial: Z5H7KLF9FSAA[/INDENT]
[INDENT=3]             size: 3726GiB (4TB)[/INDENT]
[INDENT=3]             capabilities: gpt-1.00 partitioned partitioned:gpt[/INDENT]
[INDENT=3]             configuration: ansiversion=5 guid=2b4b781d-5148-4b21-b9b2-5d80be3a2b5d logicalsectorsize=512 sectorsize=4096[/INDENT]
[INDENT=3]           *-volume[/INDENT]
[INDENT=3]                description: EFI partition[/INDENT]
[INDENT=3]                physical id: 1[/INDENT]
[INDENT=3]                bus info: scsi@2:0.0.0,1[/INDENT]
[INDENT=3]                logical name: /dev/sdc1[/INDENT]
[INDENT=3]                serial: 56a04f45-087e-43cf-b0fd-7100811ad04a[/INDENT]
[INDENT=3]                capacity: 3726GiB
 [/INDENT]






[ATTACH=CONFIG]287700[/ATTACH]

Thanks.

---

### Post by alessandro4891 on 2021-01-08
I'm seriously convinced that the system disk is corrupted:

nas@ubuntu:/$ ls
**?????????8**
bin
boot
**d**
dev
**d???????p????????????????????????????t?????p?????p???????????????d**
etc
home
initrd.img
initrd.img.old
lib
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
snap
srv
sys
**t?M??9m??ay??9?R???X{?ML59??**
tmp
usr
var
vmlinuz
vmlinuz.old


I have no idea of file in bold character.
I'll wait your supports.
Thanks.

---

