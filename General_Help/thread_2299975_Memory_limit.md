---
title: "Memory limit"
date: 2015-10-22
forum: General Help
---

### Post by alterpub on 2015-10-22
Hi,
My situation following:
```
[root@itsb tmp]# grep -i memtotal /proc/meminfo
MemTotal:        3977596 kB
[root@itsb tmp]# uname -m
x86_64
[root@itsb tmp]# lshw -short | grep 'System\ Memory'
/0/28                    memory         8GiB System Memory
```

so you can see that I have 64bit system, lshw and BIOS detect that I have 8Gb ram, but system shows and use only 4Gb.

```
[root@itsb boot]# lshw -C memory
  *-firmware
       description: BIOS
       vendor: Intel Corp.
       physical id: 0
       version: TCIBX10H.86A.0048.2011.1206.1342
       date: 12/06/2011
       size: 64KiB
       capacity: 960KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: internal varies instruction
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3-Cache
       size: 8MiB
       capacity: 8MiB
       capabilities: internal instruction
  *-memory
       description: System Memory
       physical id: 28
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
          product: 256M6408V69AD2J15E
          vendor: Undefined
          physical id: 0
          serial: E7511712
          slot: CHANNEL A
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
          product: 9905403-137.A00LF
          vendor: Kingston
          physical id: 1
          serial: 673C4D98
          slot: CHANNEL A
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:2
          description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
          product: M378B5773CH0-CH9
          vendor: Undefined
          physical id: 2
          serial: 638CCB19
          slot: CHANNEL B
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:3
          description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
          product: 9905403-137.A00LF
          vendor: Kingston
          physical id: 3
          serial: 653C4098
          slot: CHANNEL B
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
```

I've Intel DH55HC motherboard and i5-750 CPU, also I've setup the latest BIOS firmware from Intel site, but it's old enough (2011 year), and there is no memory remap feature.

I tried to add mem=8192M to grub, but it's a limit from top side, so there wasn't any effect.
I've setup the latest kernel from ubuntu's mainline repository [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-rc6-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-rc6-unstable/) and it didn't give any effect too.

I've no ideas anymore, please help me.

ubuntu 14.04.2
```
uname -a 
Linux itsb.pro 4.3.0-040300rc6-generic #201510182030 SMP Mon Oct 19 00:31:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
ls -1 /boot/vmlinuz*
/boot/vmlinuz-3.13.0-66-generic
/boot/vmlinuz-3.19.0-31-generic
/boot/vmlinuz-4.0.9-040009-generic
/boot/vmlinuz-4.3.0-040300rc4-generic
/boot/vmlinuz-4.3.0-040300rc6-generic
```

Also I've tried to add to grub such options like: "forcepae -- forcepae", disable_mtrr_trim, mem=8G

---

### Post by tgalati4 on 2015-10-23
It could be a limit on the Intel motherboard southbridge.  High-density chips on the RAM sticks could limit memory access.  Run memtest.  How much memory is shown?

---

### Post by Doug S on 2015-10-23
I don't know if it will provide any more insight, but what do you get for this:```
$ [COLOR="#FF0000"]grep Memory /var/log/kern.log[/COLOR]
Oct 18 10:25:27 s15 kernel: [    0.000000] Memory: 15981096K/16472972K available (7901K kernel code, 1265K rwdata, 3864K rodata, 1460K init, 1300K bss, 491876K reserved, 0K cma-reserved)
Oct 18 10:25:28 s15 kernel: [   13.136344] [drm] Memory usable by graphics device = 2048M
```

EDIT: Out of curiosity, I wondered why the 15981096K from above was different than this (from the OP stuff above):```
$ [COLOR="#FF0000"]grep -i memtotal /proc/meminfo[/COLOR]
MemTotal:       16001404 kB

```However everything works out exactly if I look further at memory that is freed later in the boot cycle:```
$[COLOR="#FF0000"] grep Freeing /var/log/kern.log[/COLOR]
Oct 18 10:25:27 s15 kernel: [    0.009712] Freeing SMP alternatives memory: 28K (ffffffff81eab000 - ffffffff81eb2000)
Oct 18 10:25:27 s15 kernel: [    0.651792] Freeing initrd memory: 18308K (ffff880035c2e000 - ffff880036e0f000)
Oct 18 10:25:27 s15 kernel: [    3.800144] Freeing unused kernel memory: 1460K (ffffffff81d3e000 - ffffffff81eab000)
Oct 18 10:25:27 s15 kernel: [    3.842544] Freeing unused kernel memory: 280K (ffff8800017ba000 - ffff880001800000)
Oct 18 10:25:27 s15 kernel: [    3.864513] Freeing unused kernel memory: 232K (ffff880001bc6000 - ffff880001c00000)

```16001404 = 15981096 + 28 + 18308 + 1460 + 280 + 232

---

### Post by alterpub on 2015-10-24
You're not rigth, because if you have 8GB, it'll show you 7GB, but not 3.8GB.

But I've found solution, it was issue with memory sticks, I've changed 2 undefined memory sticks to Kingston and now system see all memory.

---

