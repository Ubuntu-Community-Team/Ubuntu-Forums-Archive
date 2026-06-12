---
title: "How to enable hibernation on Ubuntu 21"
date: 2021-08-21
forum: General Help
---

### Post by ayzx2 on 2021-08-21
I have tried few forums but my hibernation doesn't work. 

[https://askubuntu.com/questions/1240123/how-to-enable-hibernate-option-in-ubuntu-20-04](https://askubuntu.com/questions/1240123/how-to-enable-hibernate-option-in-ubuntu-20-04)

I am using /swapfile. The [HTML]uswsusp[/HTML] can't be installed giving me 

```
Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
Package uswsusp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'uswsusp' has no installation candidate



```
After turning the laptop on, all of the running files are gone. It seems like it have turned off an on.

```

lsb_release -a

No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 21.04
Release:    21.04
Codename:    hirsute
ayaz@ayaz-HP-Laptop-15s

```

```

lscpu

Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          4
On-line CPU(s) list:             0-3
Thread(s) per core:              2
Core(s) per socket:              2
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           140
Model name:                      11th Gen Intel(R) Core(TM) i3-1115G4 @ 3.00GHz
Stepping:                        1
CPU MHz:                         3000.000
CPU max MHz:                     4100.0000
CPU min MHz:                     400.0000
BogoMIPS:                        5990.40
Virtualization:                  VT-x
L1d cache:                       96 KiB
L1i cache:                       64 KiB
L2 cache:                        2.5 MiB
L3 cache:                        6 MiB
NUMA node0 CPU(s):               0-3
Vulnerability Itlb multihit:     Not affected
Vulnerability L1tf:              Not affected
Vulnerability Mds:               Not affected
Vulnerability Meltdown:          Not affected
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Enhanced IBRS, IBPB conditional, RSB filling
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm p
                                 be syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aper
                                 fmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_
                                 2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb cat_l2 i
                                 nvpcid_single cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adj
                                 ust bmi1 avx2 smep bmi2 erms invpcid rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb intel_pt avx51
                                 2cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves split_lock_detect dtherm ida arat pln pts hwp hwp_notify 
                                 hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bit
                                 alg avx512_vpopcntdq rdpid movdiri movdir64b fsrm avx512_vp2intersect md_clear flush_l1d arch_capabilities



```

```

lspci

0000:00:00.0 Host bridge: Intel Corporation Device 9a04 (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation Device 9a78 (rev 01)
0000:00:04.0 Signal processing controller: Intel Corporation Device 9a03 (rev 01)
0000:00:08.0 System peripheral: Intel Corporation Device 9a11 (rev 01)
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller
0000:00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20)
0000:00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20)
0000:00:15.0 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20)
0000:00:15.1 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #1 (rev 20)
0000:00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20)
0000:00:17.0 System peripheral: Intel Corporation Device 09ab
0000:00:1d.0 PCI bridge: Intel Corporation Tiger Lake-LP PCI Express Root Port #9 (rev 20)
0000:00:1d.1 PCI bridge: Intel Corporation Device a0b1 (rev 20)
0000:00:1e.0 Communication controller: Intel Corporation Tiger Lake-LP Serial IO UART Controller #0 (rev 20)
0000:00:1e.3 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO SPI Controller #1 (rev 20)
0000:00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 20)
0000:00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20)
0000:00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20)
0000:00:1f.5 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP SPI Controller (rev 20)
0000:01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
0000:02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
10000:e0:17.0 SATA controller: Intel Corporation Device a0d3 (rev 20)

```

---

### Post by coffeecat on 2021-08-21
I can't help you with the fundamental question of how to get hibernate to work, but I've found some information about the package uswsusp. According to a search on packages.ubuntu.com - [https://packages.ubuntu.com/search?keywords=uswsusp&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=uswsusp&searchon=names&suite=all&section=all) - it's only available for the currently supported LTS releases, 18.04 and 20.04, in the Universe repository. Hence the message from the package manager in your 21.04 system. 

I also found this on Launchpad: [https://launchpad.net/ubuntu/+source/uswsusp](https://launchpad.net/ubuntu/+source/uswsusp)

It looks as though the maintainer is releasing packages for LTS versions of Ubuntu only, judging by the list on that page. Whether they will do so for 22.04 in due course remains to be seen.

Not good news I'm sorry to say, but possibly someone will have other suggestions for you not involving the uswsusp package. Unless you wish to go back to running the 20.04 LTS release.

**Edit:**  And now I find that you've already been told most of this last July: [https://ubuntuforums.org/showthread.php?t=2464460](https://ubuntuforums.org/showthread.php?t=2464460) .  You should have mentioned that you already knew that the package uswsusp was not available for 21.04 so that those trying to help you are not wasting their time re-inventing the wheel. It's called forum etiquette.

---

### Post by GhX6GZMB on 2021-08-21
I've never been able to make Hibernate work reliably with a swapfile - or even just to get it to work. And judging by the many posts on the web on this subject, I'm not alone.

Hibernation always works reliably with a swap partition, at least on my three laptops. I haven't used any "uswusp" or other programs to set it up, but did it manually. It's not hard.
Setup is not dedicated to any specific desktop environment, but the timeout or lid functions are to some extent.

---

### Post by C.S.Cameron on 2021-08-22
Did you look at my answer on that page?
For a swapfile you need a resume-offset:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX **resume_offset=XXXXX**"
```
Only two answers on that page mention this.

---

