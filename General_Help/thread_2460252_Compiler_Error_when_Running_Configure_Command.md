---
title: "Compiler Error when Running Configure Command"
date: 2021-04-05
forum: General Help
---

### Post by iamdarthmole on 2021-04-05
Trying to setup MenuMaker and keep getting the following error when running

```
./cofigure
```

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports the include directive... yes (GNU style)
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/jason/Downloads/menumaker-0.99.12':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details

```

So then I run

```
sudo apt install gcc
```

and get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version (4:9.3.0-1ubuntu2).
The following packages were automatically installed and are no longer required:
  libappindicator1 libc++1 libc++1-10 libc++abi1-10 libdbusmenu-gtk4
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

If I run 

```
sudo apt install g++
```

I also get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version (4:9.3.0-1ubuntu2).
The following packages were automatically installed and are no longer required:
  libappindicator1 libc++1 libc++1-10 libc++abi1-10 libdbusmenu-gtk4
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

If I run

```
sudo apt-get install build-essential
```

I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.8ubuntu1.1).
The following packages were automatically installed and are no longer required:
  libappindicator1 libc++1 libc++1-10 libc++abi1-10 libdbusmenu-gtk4
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

If I run 

```
g++ --version
```

I get 

```
g++ (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

If I run 

```
gcc --version
```

I get

```
Command 'gcc' not found, but can be installed with:

sudo apt install gcc
```

If I run 

```
sudo apt install gcc
```

I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version (4:9.3.0-1ubuntu2).
The following packages were automatically installed and are no longer required:
  libappindicator1 libc++1 libc++1-10 libc++abi1-10 libdbusmenu-gtk4
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I have had other issues trying to compile files for other apps/programs so I don't think this is an issue with MenuMake specifically, though I'm a newb so I could be wrong. Any assistance is greatly appreciated!

This is part of my lshw output, wasn't sure if I should post all of it.

```
description: Notebook    product: XPS 13 9310 (0991)
    vendor: Dell Inc.
    serial: 30C4593
    width: 64 bits
    capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=XPS sku=0991 uuid=44454C4C-3000-1043-8034-B3C04F353933
  *-core
       description: Motherboard
       product: 0THX8P
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: /30C4593/CNCMK000C1005C/
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: 2.0.0
          date: 01/28/2021
          size: 1MiB
          capacity: 32MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: 11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1834MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb cat_l2 invpcid_single cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb intel_pt avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq rdpid movdiri movdir64b fsrm avx512_vp2intersect md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=4 enabledcores=4 threads=8
```

---

### Post by iamdarthmole on 2021-04-05
Had to run ```
sudo ln -s /usr/bin/gcc-9 /usr/bin/gcc
``` to create a missing relationship. Installed after that. Some Discord server friends helped.

---

