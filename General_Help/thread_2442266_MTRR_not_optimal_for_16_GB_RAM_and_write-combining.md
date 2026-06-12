---
title: "MTRR not optimal for 16 GB RAM and write-combining missing for Video"
date: 2020-05-01
forum: General Help
---

### Post by &amp;wP*!) on 2020-05-01
Hi all,

Setup
[LIST]
[*] CPU: Intel i7-4600U 
[*] Video: Intel HD 4400 Haswell-ULT Integrated Graphics Controller (lshw -c display: vmemory:f7800000-f7bfffff memory:e0000000-efffffff )
[*] RAM: 16GB
[*] Distro: Lubuntu 19.04
[*] Kernel Linux host-lubuntu 5.0.0-38-generic #41-Ubuntu SMP Tue Dec 3 00:27:35 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
[*] Video driver i915 1.6.0 20181204 for 0000:00:02.0 on minor 0
[/LIST]
Problems
[LIST=1]
[*]Kernel cannot find optimal values for the settings mtrr_gran_size + mtrr_chunk_size in this setup.
[*]Video RAM is not mapped to a write-combining area.
[*]Same problem with Ubuntu 20.04 (Live CD)
[/LIST]
Snapshot from dmesg:
```

[    0.000872] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000997] total RAM covered: 16318M
[    0.001172]  gran_size: 64K  chunk_size: 64K         num_reg: 10     lose cover RAM: 110M
[    0.001173]  gran_size: 64K  chunk_size: 128K        num_reg: 10     lose cover RAM: 110M
[    0.001174]  gran_size: 64K  chunk_size: 256K        num_reg: 10     lose cover RAM: 110M
[    0.001174]  gran_size: 64K  chunk_size: 512K        num_reg: 10     lose cover RAM: 110M
[    0.001175]  gran_size: 64K  chunk_size: 1M  num_reg: 10     lose cover RAM: 110M
[    0.001176]  gran_size: 64K  chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001177]  gran_size: 64K  chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001177]  gran_size: 64K  chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001178]  gran_size: 64K  chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001179] *BAD*gran_size: 64K      chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[COLOR="#FF0000"][B][    0.001180]  gran_size: 64K  chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001180]  gran_size: 64K  chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001181]  gran_size: 64K  chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001182]  gran_size: 64K  chunk_size: 512M        num_reg: 10     lose cover RAM: 0G[/B][/COLOR]
[    0.001182]  gran_size: 64K  chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001183] *BAD*gran_size: 64K      chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001184]  gran_size: 128K         chunk_size: 128K        num_reg: 10     lose cover RAM: 110M
[    0.001185]  gran_size: 128K         chunk_size: 256K        num_reg: 10     lose cover RAM: 110M
[    0.001185]  gran_size: 128K         chunk_size: 512K        num_reg: 10     lose cover RAM: 110M
[    0.001186]  gran_size: 128K         chunk_size: 1M  num_reg: 10     lose cover RAM: 110M
[    0.001187]  gran_size: 128K         chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001187]  gran_size: 128K         chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001188]  gran_size: 128K         chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001189]  gran_size: 128K         chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001189] *BAD*gran_size: 128K     chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001190]  gran_size: 128K         chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001191]  gran_size: 128K         chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001191]  gran_size: 128K         chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001192]  gran_size: 128K         chunk_size: 512M        num_reg: 10     lose cover RAM: 0G
[    0.001193]  gran_size: 128K         chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001193] *BAD*gran_size: 128K     chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001194]  gran_size: 256K         chunk_size: 256K        num_reg: 10     lose cover RAM: 110M
[    0.001195]  gran_size: 256K         chunk_size: 512K        num_reg: 10     lose cover RAM: 110M
[    0.001195]  gran_size: 256K         chunk_size: 1M  num_reg: 10     lose cover RAM: 110M
[    0.001196]  gran_size: 256K         chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001197]  gran_size: 256K         chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001197]  gran_size: 256K         chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001198]  gran_size: 256K         chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001199] *BAD*gran_size: 256K     chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001200]  gran_size: 256K         chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001200]  gran_size: 256K         chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001201]  gran_size: 256K         chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001201]  gran_size: 256K         chunk_size: 512M        num_reg: 10     lose cover RAM: 0G
[    0.001202]  gran_size: 256K         chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001203] *BAD*gran_size: 256K     chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001204]  gran_size: 512K         chunk_size: 512K        num_reg: 10     lose cover RAM: 110M
[    0.001204]  gran_size: 512K         chunk_size: 1M  num_reg: 10     lose cover RAM: 110M
[    0.001205]  gran_size: 512K         chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001206]  gran_size: 512K         chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001206]  gran_size: 512K         chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001207]  gran_size: 512K         chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001208] *BAD*gran_size: 512K     chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001208]  gran_size: 512K         chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001209]  gran_size: 512K         chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001210]  gran_size: 512K         chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001210]  gran_size: 512K         chunk_size: 512M        num_reg: 10     lose cover RAM: 0G
[    0.001211]  gran_size: 512K         chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001212] *BAD*gran_size: 512K     chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001212]  gran_size: 1M   chunk_size: 1M  num_reg: 10     lose cover RAM: 110M
[    0.001213]  gran_size: 1M   chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001214]  gran_size: 1M   chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001214]  gran_size: 1M   chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001215]  gran_size: 1M   chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001216] *BAD*gran_size: 1M       chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001216]  gran_size: 1M   chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001217]  gran_size: 1M   chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001218]  gran_size: 1M   chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001218]  gran_size: 1M   chunk_size: 512M        num_reg: 10     lose cover RAM: 0G
[    0.001219]  gran_size: 1M   chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001220] *BAD*gran_size: 1M       chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001220]  gran_size: 2M   chunk_size: 2M  num_reg: 10     lose cover RAM: 110M
[    0.001221]  gran_size: 2M   chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001222]  gran_size: 2M   chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001222]  gran_size: 2M   chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001223] *BAD*gran_size: 2M       chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001224]  gran_size: 2M   chunk_size: 64M         num_reg: 10     lose cover RAM: 0G
[    0.001224]  gran_size: 2M   chunk_size: 128M        num_reg: 10     lose cover RAM: 0G
[    0.001225]  gran_size: 2M   chunk_size: 256M        num_reg: 10     lose cover RAM: 0G
[    0.001226]  gran_size: 2M   chunk_size: 512M        num_reg: 10     lose cover RAM: 0G
[    0.001226]  gran_size: 2M   chunk_size: 1G  num_reg: 10     lose cover RAM: 0G
[    0.001227] *BAD*gran_size: 2M       chunk_size: 2G  num_reg: 10     lose cover RAM: -1G
[    0.001228]  gran_size: 4M   chunk_size: 4M  num_reg: 10     lose cover RAM: 110M
[    0.001228]  gran_size: 4M   chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001229]  gran_size: 4M   chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001230] *BAD*gran_size: 4M       chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001230]  gran_size: 4M   chunk_size: 64M         num_reg: 10     lose cover RAM: 2M
[    0.001231]  gran_size: 4M   chunk_size: 128M        num_reg: 10     lose cover RAM: 2M
[    0.001232]  gran_size: 4M   chunk_size: 256M        num_reg: 10     lose cover RAM: 2M
[    0.001232]  gran_size: 4M   chunk_size: 512M        num_reg: 10     lose cover RAM: 2M
[    0.001233]  gran_size: 4M   chunk_size: 1G  num_reg: 10     lose cover RAM: 2M
[    0.001234] *BAD*gran_size: 4M       chunk_size: 2G  num_reg: 10     lose cover RAM: -1022M
[    0.001234]  gran_size: 8M   chunk_size: 8M  num_reg: 10     lose cover RAM: 110M
[    0.001235]  gran_size: 8M   chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001236] *BAD*gran_size: 8M       chunk_size: 32M         num_reg: 10     lose cover RAM: -18M
[    0.001236]  gran_size: 8M   chunk_size: 64M         num_reg: 10     lose cover RAM: 6M
[    0.001237]  gran_size: 8M   chunk_size: 128M        num_reg: 10     lose cover RAM: 6M
[    0.001238]  gran_size: 8M   chunk_size: 256M        num_reg: 10     lose cover RAM: 6M
[    0.001238]  gran_size: 8M   chunk_size: 512M        num_reg: 10     lose cover RAM: 6M
[    0.001239]  gran_size: 8M   chunk_size: 1G  num_reg: 10     lose cover RAM: 6M
[    0.001240] *BAD*gran_size: 8M       chunk_size: 2G  num_reg: 10     lose cover RAM: -1018M
[    0.001240]  gran_size: 16M  chunk_size: 16M         num_reg: 10     lose cover RAM: 110M
[    0.001241]  gran_size: 16M  chunk_size: 32M         num_reg: 10     lose cover RAM: 238M
[    0.001242]  gran_size: 16M  chunk_size: 64M         num_reg: 9      lose cover RAM: 14M
[    0.001242]  gran_size: 16M  chunk_size: 128M        num_reg: 9      lose cover RAM: 14M
[    0.001243]  gran_size: 16M  chunk_size: 256M        num_reg: 9      lose cover RAM: 14M
[    0.001244]  gran_size: 16M  chunk_size: 512M        num_reg: 9      lose cover RAM: 14M
[    0.001244]  gran_size: 16M  chunk_size: 1G  num_reg: 9      lose cover RAM: 14M
[    0.001245]  gran_size: 16M  chunk_size: 2G  num_reg: 10     lose cover RAM: 14M
[    0.001246]  gran_size: 32M  chunk_size: 32M         num_reg: 10     lose cover RAM: 62M
[    0.001246]  gran_size: 32M  chunk_size: 64M         num_reg: 9      lose cover RAM: 30M
[    0.001247]  gran_size: 32M  chunk_size: 128M        num_reg: 8      lose cover RAM: 30M
[    0.001248]  gran_size: 32M  chunk_size: 256M        num_reg: 8      lose cover RAM: 30M
[    0.001248]  gran_size: 32M  chunk_size: 512M        num_reg: 8      lose cover RAM: 30M
[    0.001249]  gran_size: 32M  chunk_size: 1G  num_reg: 8      lose cover RAM: 30M
[    0.001250]  gran_size: 32M  chunk_size: 2G  num_reg: 9      lose cover RAM: 30M
[    0.001250]  gran_size: 64M  chunk_size: 64M         num_reg: 10     lose cover RAM: 62M
[    0.001251]  gran_size: 64M  chunk_size: 128M        num_reg: 8      lose cover RAM: 62M
[    0.001252]  gran_size: 64M  chunk_size: 256M        num_reg: 8      lose cover RAM: 62M
[    0.001252]  gran_size: 64M  chunk_size: 512M        num_reg: 8      lose cover RAM: 62M
[    0.001253]  gran_size: 64M  chunk_size: 1G  num_reg: 8      lose cover RAM: 62M
[    0.001254]  gran_size: 64M  chunk_size: 2G  num_reg: 9      lose cover RAM: 62M
[    0.001254]  gran_size: 128M         chunk_size: 128M        num_reg: 8      lose cover RAM: 190M
[    0.001255]  gran_size: 128M         chunk_size: 256M        num_reg: 8      lose cover RAM: 190M
[    0.001256]  gran_size: 128M         chunk_size: 512M        num_reg: 8      lose cover RAM: 190M
[    0.001256]  gran_size: 128M         chunk_size: 1G  num_reg: 8      lose cover RAM: 190M
[    0.001257]  gran_size: 128M         chunk_size: 2G  num_reg: 9      lose cover RAM: 190M
[    0.001258]  gran_size: 256M         chunk_size: 256M        num_reg: 6      lose cover RAM: 446M
[    0.001258]  gran_size: 256M         chunk_size: 512M        num_reg: 8      lose cover RAM: 446M
[    0.001259]  gran_size: 256M         chunk_size: 1G  num_reg: 8      lose cover RAM: 446M
[    0.001260]  gran_size: 256M         chunk_size: 2G  num_reg: 9      lose cover RAM: 446M
[    0.001260]  gran_size: 512M         chunk_size: 512M        num_reg: 4      lose cover RAM: 958M
[    0.001261]  gran_size: 512M         chunk_size: 1G  num_reg: 4      lose cover RAM: 958M
[    0.001262]  gran_size: 512M         chunk_size: 2G  num_reg: 4      lose cover RAM: 958M
[    0.001262]  gran_size: 1G   chunk_size: 1G  num_reg: 4      lose cover RAM: 958M
[    0.001263]  gran_size: 1G   chunk_size: 2G  num_reg: 4      lose cover RAM: 958M
[    0.001264]  gran_size: 2G   chunk_size: 2G  num_reg: 3      lose cover RAM: 1982M
[    0.001264] mtrr_cleanup: can not find optimal value
[    0.001265] please specify mtrr_gran_size/mtrr_chunk_size
```

MTRR says 3 registers are not used. and None of the 6 available ones map the region of Video RAM for write-combining, which could have been interesting for Video.
```
$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=16384MB, count=1: write-back
reg01: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg02: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg04: base=0x0dd000000 ( 3536MB), size=   16MB, count=1: uncachable
reg05: base=0x41f000000 (16880MB), size=   16MB, count=1: uncachable
reg06: base=0x41ee00000 (16878MB), size=    2MB, count=1: uncachable
```
Kernel configuration parameters are
```
$ grep -i mtrr /usr/src/linux-headers-5.0.0-38-generic/.config
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=1
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1
```

Questions
[LIST=1]
[*]Why does the sanitizer not choose one of the options below which result uncovered RAM is 0GB? (see red text in the dmesg dump)
[*]Is it a good practice to change these settings? If yes, what values mtrr_gran_size and mtrr_chunk_size are meaningful?
[*][Several hardware probe reports]("https://linux-hardware.org/index.php?view=computers&vendor=Dell&model=Latitude+E7440") from the same laptop model show none of the laptops with 16GB RAM has a solution for this (most reports are using quite new kernels 5.x). Laptops with 4GB and 8GB RAM do not have this issue. Did not look at the other laptop vendors. I have doubts that default kernel settings support 16GB. Can you confirm this? The processor supports up to 16 GB RAM (see the Intel link below).
[*]Why does the kernel not map the Video RAM area vmemory:f7800000-f7bfffff memory:e0000000-efffffff not to a write-combining area, which could have been defined by an unused MTRR?
[*][Intel® Core™ i7-4600U Processor]("https://ark.intel.com/content/www/us/en/ark/products/76616/intel-core-i7-4600u-processor-4m-cache-up-to-3-30-ghz.html?wapkw=i7-4600u") states that the graphics controller can address up to 2 GB. 16GB RAM is quite enough to support this. Why does the kernel assign 256MB despite that? memory:e0000000-efffffff gives this value) Is this is a restriction of i915 driver?
[/LIST]

Kernel doc [https://www.kernel.org/doc/html/v4.14/admin-guide/kernel-parameters.html](https://www.kernel.org/doc/html/v4.14/admin-guide/kernel-parameters.html) contains little information about this.

---

### Post by Impavidus on 2020-05-01
I'm not familiar with the finer details of memory management, so I can't help you with that, but do you realise that 19.04 reached end of life over three months ago?

---

### Post by &amp;wP*!) on 2020-05-01
> **Impavidus said:**
> I'm not familiar with the finer details of memory management, so I can't help you with that, but do you realise that 19.04 reached end of life over three months ago?

See item 3 in Problem section. Ubuntu 20.04 has the same problem. During the boot sequence of 20.04 Live CD, dmesg shows exactly the same messages.

---

### Post by CelticWarrior on 2020-05-01
> **pencuse said:**
> See item 3 in Problem section. Ubuntu 20.04 has the same problem. During the boot sequence of 20.04 Live CD, dmesg shows exactly the same messages.

So you should install 20.04 (or any other supported release) and troubleshoot from there. That the same problem persists in the current release is no excuse to keep an unsupported one.

---

### Post by &amp;wP*!) on 2020-05-01
> **CelticWarrior said:**
> So you should install 20.04 (or any other supported release) and troubleshoot from there. That the same problem persists in the current release is no excuse to keep an unsupported one.

Apologize for not being clear. Now I have installed 20.04 on the computer. Proof:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
$ uname -a
Linux e7440 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


```
Ubuntu 20.04 definitely has this problem.

**Setup**
[LIST=1]
[*]CPU: Intel i7-4600U
[*]Video: Intel HD 4400 Haswell-ULT Integrated Graphics Controller (lshw -c display: resources: irq:49 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff)
[*]RAM: 16GB
[*]Distro: Lubuntu 20.04
[*]Kernel: Linux e7440 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[*]Video driver: [    0.840689] [drm] Initialized i915 1.6.0 20190822 for 0000:00:02.0 on minor 0
[*][/LIST]
Here are the problems for 20.04:
[LIST=1]
[*]Kernel cannot find optimal values for the settings mtrr_gran_size + mtrr_chunk_size in this setup.
[*]Video RAM is not mapped to a write-combining area.
[/LIST]
Below the dmesg snapshot:
```
[    0.000071] MTRR default type: uncachable
[    0.000071] MTRR fixed ranges enabled:
[    0.000072]   00000-9FFFF write-back
[    0.000073]   A0000-DFFFF uncachable
[    0.000074]   E0000-FFFFF write-protect
[    0.000074] MTRR variable ranges enabled:
[    0.000075]   0 base 0000000000 mask 7C00000000 write-back
[    0.000076]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000077]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000078]   3 base 00DE000000 mask 7FFE000000 uncachable
[    0.000078]   4 base 00DD000000 mask 7FFF000000 uncachable
[    0.000079]   5 base 041F000000 mask 7FFF000000 uncachable
[    0.000079]   6 base 041EE00000 mask 7FFFE00000 uncachable
[    0.000080]   7 disabled
[    0.000080]   8 disabled
[    0.000081]   9 disabled
[    0.000360] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000477] total RAM covered: 16318M
[    0.000654]  gran_size: 64K 	chunk_size: 64K 	num_reg: 10  	lose cover RAM: 110M
[    0.000655]  gran_size: 64K 	chunk_size: 128K 	num_reg: 10  	lose cover RAM: 110M
[    0.000656]  gran_size: 64K 	chunk_size: 256K 	num_reg: 10  	lose cover RAM: 110M
[    0.000657]  gran_size: 64K 	chunk_size: 512K 	num_reg: 10  	lose cover RAM: 110M
[    0.000657]  gran_size: 64K 	chunk_size: 1M 	num_reg: 10  	lose cover RAM: 110M
[    0.000658]  gran_size: 64K 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000659]  gran_size: 64K 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000659]  gran_size: 64K 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000660]  gran_size: 64K 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000661] *BAD*gran_size: 64K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000661]  gran_size: 64K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000662]  gran_size: 64K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000663]  gran_size: 64K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000664]  gran_size: 64K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000664]  gran_size: 64K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000665] *BAD*gran_size: 64K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000666]  gran_size: 128K 	chunk_size: 128K 	num_reg: 10  	lose cover RAM: 110M
[    0.000666]  gran_size: 128K 	chunk_size: 256K 	num_reg: 10  	lose cover RAM: 110M
[    0.000667]  gran_size: 128K 	chunk_size: 512K 	num_reg: 10  	lose cover RAM: 110M
[    0.000668]  gran_size: 128K 	chunk_size: 1M 	num_reg: 10  	lose cover RAM: 110M
[    0.000668]  gran_size: 128K 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000669]  gran_size: 128K 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000670]  gran_size: 128K 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000670]  gran_size: 128K 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000671] *BAD*gran_size: 128K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000672]  gran_size: 128K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000672]  gran_size: 128K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000673]  gran_size: 128K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000674]  gran_size: 128K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000674]  gran_size: 128K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000675] *BAD*gran_size: 128K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000676]  gran_size: 256K 	chunk_size: 256K 	num_reg: 10  	lose cover RAM: 110M
[    0.000676]  gran_size: 256K 	chunk_size: 512K 	num_reg: 10  	lose cover RAM: 110M
[    0.000677]  gran_size: 256K 	chunk_size: 1M 	num_reg: 10  	lose cover RAM: 110M
[    0.000678]  gran_size: 256K 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000678]  gran_size: 256K 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000679]  gran_size: 256K 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000680]  gran_size: 256K 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000680] *BAD*gran_size: 256K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000681]  gran_size: 256K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000682]  gran_size: 256K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000682]  gran_size: 256K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000683]  gran_size: 256K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000684]  gran_size: 256K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000684] *BAD*gran_size: 256K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000685]  gran_size: 512K 	chunk_size: 512K 	num_reg: 10  	lose cover RAM: 110M
[    0.000686]  gran_size: 512K 	chunk_size: 1M 	num_reg: 10  	lose cover RAM: 110M
[    0.000686]  gran_size: 512K 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000687]  gran_size: 512K 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000688]  gran_size: 512K 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000688]  gran_size: 512K 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000689] *BAD*gran_size: 512K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000690]  gran_size: 512K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000690]  gran_size: 512K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000691]  gran_size: 512K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000692]  gran_size: 512K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000692]  gran_size: 512K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000693] *BAD*gran_size: 512K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000694]  gran_size: 1M 	chunk_size: 1M 	num_reg: 10  	lose cover RAM: 110M
[    0.000695]  gran_size: 1M 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000695]  gran_size: 1M 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000696]  gran_size: 1M 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000696]  gran_size: 1M 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000697] *BAD*gran_size: 1M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[B][COLOR="#FF0000"][    0.000698]  gran_size: 1M 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000699]  gran_size: 1M 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000699]  gran_size: 1M 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000700]  gran_size: 1M 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000701]  gran_size: 1M 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G[/COLOR][/B]
[    0.000701] *BAD*gran_size: 1M 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000702]  gran_size: 2M 	chunk_size: 2M 	num_reg: 10  	lose cover RAM: 110M
[    0.000703]  gran_size: 2M 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000703]  gran_size: 2M 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000704]  gran_size: 2M 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000705] *BAD*gran_size: 2M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000705]  gran_size: 2M 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 0G
[    0.000706]  gran_size: 2M 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000707]  gran_size: 2M 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000707]  gran_size: 2M 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000708]  gran_size: 2M 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000709] *BAD*gran_size: 2M 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000709]  gran_size: 4M 	chunk_size: 4M 	num_reg: 10  	lose cover RAM: 110M
[    0.000710]  gran_size: 4M 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000711]  gran_size: 4M 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000711] *BAD*gran_size: 4M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000712]  gran_size: 4M 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 2M
[    0.000713]  gran_size: 4M 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 2M
[    0.000713]  gran_size: 4M 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 2M
[    0.000714]  gran_size: 4M 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 2M
[    0.000714]  gran_size: 4M 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 2M
[    0.000715] *BAD*gran_size: 4M 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1022M
[    0.000716]  gran_size: 8M 	chunk_size: 8M 	num_reg: 10  	lose cover RAM: 110M
[    0.000716]  gran_size: 8M 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000717] *BAD*gran_size: 8M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -18M
[    0.000718]  gran_size: 8M 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 6M
[    0.000718]  gran_size: 8M 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 6M
[    0.000719]  gran_size: 8M 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 6M
[    0.000720]  gran_size: 8M 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 6M
[    0.000720]  gran_size: 8M 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 6M
[    0.000721] *BAD*gran_size: 8M 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1018M
[    0.000722]  gran_size: 16M 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: 110M
[    0.000722]  gran_size: 16M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: 238M
[    0.000723]  gran_size: 16M 	chunk_size: 64M 	num_reg: 9  	lose cover RAM: 14M
[    0.000724]  gran_size: 16M 	chunk_size: 128M 	num_reg: 9  	lose cover RAM: 14M
[    0.000725]  gran_size: 16M 	chunk_size: 256M 	num_reg: 9  	lose cover RAM: 14M
[    0.000725]  gran_size: 16M 	chunk_size: 512M 	num_reg: 9  	lose cover RAM: 14M
[    0.000726]  gran_size: 16M 	chunk_size: 1G 	num_reg: 9  	lose cover RAM: 14M
[    0.000727]  gran_size: 16M 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: 14M
[    0.000727]  gran_size: 32M 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: 62M
[    0.000728]  gran_size: 32M 	chunk_size: 64M 	num_reg: 9  	lose cover RAM: 30M
[    0.000729]  gran_size: 32M 	chunk_size: 128M 	num_reg: 8  	lose cover RAM: 30M
[    0.000729]  gran_size: 32M 	chunk_size: 256M 	num_reg: 8  	lose cover RAM: 30M
[    0.000730]  gran_size: 32M 	chunk_size: 512M 	num_reg: 8  	lose cover RAM: 30M
[    0.000731]  gran_size: 32M 	chunk_size: 1G 	num_reg: 8  	lose cover RAM: 30M
[    0.000731]  gran_size: 32M 	chunk_size: 2G 	num_reg: 9  	lose cover RAM: 30M
[    0.000732]  gran_size: 64M 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: 62M
[    0.000733]  gran_size: 64M 	chunk_size: 128M 	num_reg: 8  	lose cover RAM: 62M
[    0.000733]  gran_size: 64M 	chunk_size: 256M 	num_reg: 8  	lose cover RAM: 62M
[    0.000734]  gran_size: 64M 	chunk_size: 512M 	num_reg: 8  	lose cover RAM: 62M
[    0.000734]  gran_size: 64M 	chunk_size: 1G 	num_reg: 8  	lose cover RAM: 62M
[    0.000735]  gran_size: 64M 	chunk_size: 2G 	num_reg: 9  	lose cover RAM: 62M
[    0.000736]  gran_size: 128M 	chunk_size: 128M 	num_reg: 8  	lose cover RAM: 190M
[    0.000736]  gran_size: 128M 	chunk_size: 256M 	num_reg: 8  	lose cover RAM: 190M
[    0.000737]  gran_size: 128M 	chunk_size: 512M 	num_reg: 8  	lose cover RAM: 190M
[    0.000738]  gran_size: 128M 	chunk_size: 1G 	num_reg: 8  	lose cover RAM: 190M
[    0.000739]  gran_size: 128M 	chunk_size: 2G 	num_reg: 9  	lose cover RAM: 190M
[    0.000739]  gran_size: 256M 	chunk_size: 256M 	num_reg: 6  	lose cover RAM: 446M
[    0.000740]  gran_size: 256M 	chunk_size: 512M 	num_reg: 8  	lose cover RAM: 446M
[    0.000740]  gran_size: 256M 	chunk_size: 1G 	num_reg: 8  	lose cover RAM: 446M
[    0.000741]  gran_size: 256M 	chunk_size: 2G 	num_reg: 9  	lose cover RAM: 446M
[    0.000742]  gran_size: 512M 	chunk_size: 512M 	num_reg: 4  	lose cover RAM: 958M
[    0.000742]  gran_size: 512M 	chunk_size: 1G 	num_reg: 4  	lose cover RAM: 958M
[    0.000743]  gran_size: 512M 	chunk_size: 2G 	num_reg: 4  	lose cover RAM: 958M
[    0.000744]  gran_size: 1G 	chunk_size: 1G 	num_reg: 4  	lose cover RAM: 958M
[    0.000744]  gran_size: 1G 	chunk_size: 2G 	num_reg: 4  	lose cover RAM: 958M
[    0.000745]  gran_size: 2G 	chunk_size: 2G 	num_reg: 3  	lose cover RAM: 1982M
[    0.000746] mtrr_cleanup: can not find optimal value
[    0.000746] please specify mtrr_gran_size/mtrr_chunk_size
```
MTRR registers:
```
$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=16384MB, count=1: write-back
reg01: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg02: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg04: base=0x0dd000000 ( 3536MB), size=   16MB, count=1: uncachable
reg05: base=0x41f000000 (16880MB), size=   16MB, count=1: uncachable
reg06: base=0x41ee00000 (16878MB), size=    2MB, count=1: uncachable
```
Kernel configuration parameters
```
$ grep -i mtrr /usr/src/linux-headers-5.4.0-28-generic/.config
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=1
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1
```

Questions for 20.04
[LIST=1]
[*]Why does the sanitizer not choose one of the options below which result uncovered RAM is 0GB? (see red text in the dmesg dump)
[*]Is it a good practice to change these settings? If yes, what values mtrr_gran_size and mtrr_chunk_size are meaningful?
[*][Several hardware probe reports from the same laptop model]("https://linux-hardware.org/index.php?view=computers&vendor=Dell&model=Latitude+E7440") show none of the laptops with 16GB RAM has a solution for this (most reports are using quite new kernels 5.x). Laptops with 4GB and 8GB RAM do not have this issue. Did not look at the other laptop vendors. I have doubts that default kernel settings support 16GB. Can you confirm this? The processor supports up to 16 GB RAM (see the Intel link below).
[*]Why does the kernel not map the Video RAM area vmemory:f7800000-f7bfffff memory:e0000000-efffffff not to a write-combining area, which could have been defined by an unused MTRR?
[*][Intel® Core&#8482; i7-4600U Processor]("https://ark.intel.com/content/www/us/en/ark/products/76616/intel-core-i7-4600u-processor-4m-cache-up-to-3-30-ghz.html?wapkw=i7-4600u") states that the graphics controller can address up to 2 GB. 16GB RAM is quite enough to support this. Why does the kernel assign 256MB despite that? memory:e0000000-efffffff gives this value) Is this is a restriction of i915 driver?
[/LIST]

---

