---
title: "Random kernel panic."
date: 2024-05-11
forum: General Help
---

### Post by hjorden on 2024-05-11
Fairly new, but know a bit.
I got a home server in the garage running different things , Home Assistant, a family tree and different things. Been going fine, could Google the stuff I didn't know. But now I'm in deep water.

I've upgraded from 18 I think, to 22. Everything seemed to work fine, but I get some kernel panic errors.
They come regularly, maybe once a day or every other day.

See error: [https://ibb.co/1d3jt6m](https://ibb.co/1d3jt6m)

It doesn't really tell me much. I don't really have anything to go on. I don't know what to do, to get closer to s solution.

I've cleaned up some stuff, run a RAM and HDD check without any problems.

Restarting the machine daily is driving me nuts. Any pointers and any help is greatly appreciated.

---

### Post by MAFoElffen on 2024-05-12
Is it server edition?

Please Run the UbuntuForums 'system-info' script in my signature line, and post the URL of where it uploads to.

That will tell us what your hardare is, and something about how it is installed, including the kernel boot line.

It appears to be power, pstate, and apci related. Need more info to suggest a solution.

---

### Post by hjorden on 2024-05-12
Yes it is.

I've run the script:
[https://paste.ubuntu.com/p/Yxwpz3KTkk/](https://paste.ubuntu.com/p/Yxwpz3KTkk/)
It said my system is missing some utilities, but it didn't state which ones. So I hope this is fine.

Got a new error earlier, maybe it's different: [https://ibb.co/9WxSKWd](https://ibb.co/9WxSKWd)

The help is much appreciated [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by MAFoElffen on 2024-05-12
File a Bug Report with LaunchPad.

Why am I saying this so early (in the 4th Post)?

Because look at this, in line #41 of the report:
```

 *-processor UNCLAIMED

```
I have "never" seen that before. Nor can I find that kind of error on a CPU reported anywhere on the internet. Usually devices going unclaimed are GPU's, network devices,etc. Not processors.

Let me ask a friend with an AMD CPU if he can run something and what his says...

---

### Post by Doug S on 2024-05-12
The kernel taint code codes are also a worry. Out of tree and unsigned module.

---

### Post by MAFoElffen on 2024-05-12
Been diving into some things with this "kernel stack corrupted" error...

Before blaming it on the kernel in relation to your hardware, we need to rule a few things out first.

That error often comes up when the image is corrupted due to filesystem errors or mount errors (which also points back to filesystem errors).

Is this a ext4 filesystem? Does it get this if booted from on an older kernel?

What I would try first is, if ext4, then boot from a rescue mode boot option under Grub2 > Advanced Options and do an fsck on the filesystems. If that checks out okay, then do 'network', which will remount the filesystem as r/w, then drop to a root prompt using 'root' > <Enter>, then do a reinstall of the current latest kernel... This will reinstall the latest installed kernel of releases still in support
```

VERSION=$(apt list linux-image-{5,6}* --installed 2>/dev/null | tail -n 1 | awk -F "-" '// {print $3 "-" $4}')
sudo apt install --reinstall -y linux-image-$VERSION-generic linux-headers-$VERSION-generic Linux-modules*-$VERSION-generic

```
Then test again.

If it still gets errors, then report as a Bug Report.

---

### Post by hjorden on 2024-05-13
Before the update, the kernel was 4-something, does that sound right?
I didn't get this error. Once a month or maybe every other, I lost contact to the server and had to restart. Never investigated it.

When doing fsck, I got the following:
[https://ibb.co/TbtBCFg](https://ibb.co/TbtBCFg)

When trying the update I get:
[https://paste.ubuntu.com/p/45tPWW2xF8/](https://paste.ubuntu.com/p/45tPWW2xF8/)

---

### Post by #&amp;thj^% on 2024-05-14
Please also show this:
```
 apt list nvidia* --installed

```
Your failed upgrade looks to be installing all drivers ie:
```
The following packages have unmet dependencies:
 linux-modules-nvidia-450-server-5.15.0-106-generic : Depends: nvidia-kernel-common-450-server (>= 450.248.02) but it is not installable
 linux-modules-nvidia-470-5.15.0-106-generic : Depends: nvidia-kernel-common-470 (>= 470.239.06) but it is not installable
 linux-modules-nvidia-470-server-5.15.0-106-generic : Depends: nvidia-kernel-common-470-server (>= 470.239.06) but it is not installable
 linux-modules-nvidia-535-5.15.0-106-generic : Depends: nvidia-kernel-common-535 (>= 535.171.04) but it is not installable
 linux-modules-nvidia-535-open-5.15.0-106-generic : Depends: nvidia-kernel-common-535 (<= 535.171.04-1) but it is not installable
                                                    Depends: nvidia-kernel-common-535 (>= 535.171.04) but it is not installable
 linux-modules-nvidia-535-server-5.15.0-106-generic : Depends: nvidia-kernel-common-535-server (>= 535.161.08) but it is not installable
 linux-modules-nvidia-535-server-open-5.15.0-106-generic : Depends: nvidia-kernel-common-535-server (<= 535.161.08-1) but it is not installable
                                                           Depends: nvidia-kernel-common-535-server (>= 535.161.08) but it is not installable
 linux-modules-nvidia-550-5.15.0-106-generic : Depends: nvidia-kernel-common-550 (>= 550.67) but it is not installable
 linux-modules-nvidia-550-open-5.15.0-106-generic : Depends: nvidia-kernel-common-550 (<= 550.67-1) but it is not installable
                                                    Depends: nvidia-kernel-common-550 (>= 550.67) but it is not installable
 linux-modules-nvidia-550-server-5.15.0-106-generic : Depends: nvidia-kernel-common-550-server (>= 550.54.15) but it is not installable
 linux-modules-nvidia-550-server-open-5.15.0-106-generic : Depends: nvidia-kernel-common-550-server (<= 550.54.15-1) but it is not installable
                                                           Depends: nvidia-kernel-common-550-server (>= 550.54.15) but it is not installable
E: Unable to correct problems, you have held broken packages.
```
That could and will cause corruption.

---

### Post by hjorden on 2024-05-14
Doesn't look like I have any.
I'm just getting
```
Listing... Done
```
But if thats the cause, how come the system can run fine in sometimes over a day?

---

### Post by #&amp;thj^% on 2024-05-14
I don't see how it would run period. I've not seen any Nvidia card run all drivers.
EDIT: And your system-info return MAFoElffen had you run don't even show you have an Nvidia card at all.
What recent changes have you made
Please now show this:
```
sudo apt autoremove --purge nvidia*
```

---

### Post by hjorden on 2024-05-14
That one gives me this: [https://paste.ubuntu.com/p/X76gSHgGJn/](https://paste.ubuntu.com/p/X76gSHgGJn/)

The graphics card installed, is an old one. Only installed for the initial setup, and just kept it in if i need to hook a screen to it.
The only recent change was the upgrade.

---

### Post by #&amp;thj^% on 2024-05-14
I'm still reading over all information provided so far in this thread, so I'm poking for some information that might lead to a fix.
One More please:
```
 apt -a list nvidia-kernel-common* --installed

```

---

### Post by hjorden on 2024-05-14
The help is much appreciated! :)

That one return the same as the other
```
Listing... Done
```

---

### Post by #&amp;thj^% on 2024-05-14
Ok now lets check your package-manager for updates at least.
One line at a time please:
```
sudo apt clean
sudo apt update
sudo apt upgrade
```
Post any errors if any from "upgrade" portion.

---

### Post by hjorden on 2024-05-14
No errors

```
The following NEW packages will be installed:  linux-headers-5.15.0-107 linux-headers-5.15.0-107-generic linux-image-5.15.0-107-generic linux-modules-5.15.0-107-generic linux-modules-extra-5.15.0-107-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
```

---

### Post by #&amp;thj^% on 2024-05-14
Did you take the upgrades yet? If not do so now.
Again show any errors.

---

### Post by hjorden on 2024-05-14
I did, completed without any errors.

---

### Post by #&amp;thj^% on 2024-05-14
Cool, have you rebooted yet?  if so see how long it runs now.

---

### Post by hjorden on 2024-05-14
I did, I'll post again when it dies (:

---

### Post by #&amp;thj^% on 2024-05-14
Good Deal, but before your leave will now see if your CPU is listed correctly.
```
 lshw -C cpu

```

---

### Post by hjorden on 2024-05-14
Looks the same, with the unclaimed thing. :/
```
 *-cpu
       description: CPU
       product: AMD Ryzen 5 3600X 6-Core Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 2f
       bus info: cpu@0
       version: 23.113.0
       serial: Unknown
       slot: AM4
       size: 1861MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov p  at pse36 clflush mmx fx
sr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc c  puid extd_apicid aperfm
perf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1
sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf  _lm cmp_legacy svm exta
pic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_  nb bpext perfctr_llc mw
aitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdse  ed adx smap clflushopt
clwb sha_ni xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsav  eerptr rdpru wbnoinvd a
rat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold a  vic v_vmsave_vmload vgi
f v_spec_ctrl umip rdpid overflow_recov succor smca sme sev sev_es cpufreq
       configuration: cores=6 enabledcores=6 microcode=141561875 threads=12
  *-processor UNCLAIMED
       description: SCSI Processor
       product: 91xx Config
       vendor: Marvell
       physical id: 1
       bus info: scsi@15:0.0.0
       version: 1.01
       configuration: ansiversion=5

```

---

### Post by #&amp;thj^% on 2024-05-14
Yep Bug Time, this needs a look from the kernel team.
mine:
```
 *-cpu                     
       description: CPU
       product: AMD Ryzen 5 5600H with Radeon Graphics
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: 25.80.0
       serial: Unknown
       slot: FP6
       size: 3454MHz
       capacity: 4280MHz
       width: 64 bits
       clock: 100MHz
       capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local user_shstk clzero irperf xsaveerptr rdpru wbnoinvd cppc arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif v_spec_ctrl umip pku ospke vaes vpclmulqdq rdpid overflow_recov succor smca fsrm debug_swap cpufreq
       configuration: cores=6 enabledcores=6 microcode=173015052 threads=12

```

EDIT: I wonder if that's your GPU...IJDK

@MAFoElffen this is interesting:
```
*-processor UNCLAIMED
       description: SCSI Processor
       product: 91xx Config
       vendor: Marvell
       physical id: 1
       bus info: scsi@15:0.0.0
       version: 1.01
       configuration: ansiversion=5
```

---

### Post by hjorden on 2024-05-14
Is it the graphics card? Could i just pull that out and It could be fine? As mentioned, it's an very old card.

Should I just pist a bug on launch pad as first suggested?

---

### Post by #&amp;thj^% on 2024-05-14
Wait one more day, before going for the Bug-Report.

But I'm dying to know what it would change with out that card though. as far as seeing "*-processor UNCLAIMED"

---

### Post by MAFoElffen on 2024-05-15
> **1fallen said:**
> 
EDIT: I wonder if that's your GPU...IJDK

@MAFoElffen this is interesting:
```
*-processor UNCLAIMED
       description: SCSI Processor
       product: 91xx Config
       vendor: Marvell
       physical id: 1
       bus info: scsi@15:0.0.0
       version: 1.01
       configuration: ansiversion=5
```
I looked at this last night. Is definitely a curiosity, but a distraction that is comes up under CPU.

If you notice, the vendor is "Marvell". An SCSI processor is a storage controller processor for SCSI, located on the motherboard (first made 2018). Looking up the tech specs on that board, I don't see SCSI on it(?) SCSI was more popular up through the early 2010's. Not so much these day. 

Is says it has a Marvell 90XX SCSI Processor. Those came out in 2007, but the way they applied it, was as a SAS and RAID controller.

ASUS is sort of touchy on BIOS firmware firmware. His current BIOS version is 5.13.

RE: [https://www.asus.com/motherboards-components/motherboards/prime/prime-b450m-a/helpdesk_bios/?model2Name=PRIME-B450M-A](https://www.asus.com/motherboards-components/motherboards/prime/prime-b450m-a/helpdesk_bios/?model2Name=PRIME-B450M-A)

That latest BIOS image was update on 2024.04.08... a few days ago.

I would try that first.

---

### Post by #&amp;thj^% on 2024-05-15
Yep I did some digging last nite as well came up with what you found.

I must say I'm surprised the ASUS MB even connects to it, hence all the kernel panics.
That board is a bit old I wonder how much good the firmware upgrade would help/hurt....But the upgrade should be taken regardless.

---

### Post by hjorden on 2024-05-17
Well that was a nice streak. No problems for 2 days.
This time it was new error on the screen.
```
watchdog: BUG: soft lockup - CPU# stuck for xxx seconds.
```

I tried removing the graphics card, but the[COLOR=#000000][FONT=&amp] "*-processor UNCLAIMED[/FONT][/COLOR]s" still there when running ```
[COLOR=#000000][FONT=&amp] lshw -C cpu[/FONT][/COLOR]
```

I don't know it was anything to do with anything, but the vendor was Marvell which also was the vendor of the raid controller according to the first script.
I have [this]("https://www.startech.com/en-dk/cards-adapters/pexsat32") installed which I guess is that.

---

### Post by MAFoElffen on 2024-05-18
Check the PCIe slot that is being reported: 15:0.0.0

If that is that card, it says there is a module/driver problem for that.

For what you paid for that... You could have bought a [PCIe x1 NVME M.2 adapter]("https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwi-sO27zZeGAxUAzcIEHct8DoMYABAEGgJwdg&gclid=CjwKCAjwo6GyBhBwEiwAzQTmc51wK_aSjWHOnJdV9-MhT3OFP7y1y_nudyVXXMW6bSq8RezZhkyuEBoC6isQAvD_BwE&ohost=www.google.com&cid=CAESVuD2XMKARoGzufVw2P1e5wTYBZjZoL2J4GdjGbgryPgw6oFGF4QyqaEakUv4V1FnRg0XNXgIeTwttQ1FffGVWQ70aTZmX6qPas1R_bl7vHn4zGROewZj&sig=AOD64_0neKk4hELWNwglNLsGqu4VJZtF0g&ctype=5&q=&ved=2ahUKEwjAgeW7zZeGAxUEATQIHUEIALcQ9aACKAB6BAgCEA0&adurl=") and an [NVME M.2 to SATA adapter]("https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwjTo67szZeGAxWSEq0GHd-PDL4YABAZGgJwdg&gclid=CjwKCAjwo6GyBhBwEiwAzQTmcwwL2c2VdCf08eYgX_rIy62QnaItX6GpseqXqme-x4NAXZA523CrbRoC43QQAvD_BwE&ohost=www.google.com&cid=CAESVuD2uNEtOG1P-fibCgOBMMfzdfIgovr30PREh-24yNmrUHxJlRki4Akv588T9uyuibBtHzalmdMzrfksBQcQ8KzLJrKjbMj8p2sPIx9hXsl1NMZUJMEe&sig=AOD64_19GTlblQQHIYBUqyWrdRSwb6JB9Q&ctype=5&q=&ved=2ahUKEwi8mqXszZeGAxVAMDQIHZ9OBHUQ9aACKAB6BAgBEDg&adurl=")...

But that is 1 lane. If you had a slot open with more lanes (with more throughput and bandwidth), for the same price, you could have bought a used LSI HBA that has 6-8 SATA ports, that is fully supported by Linux. (Meaning with in-kernel opensource modules/drivers...)

Based on that Bus address, and other 91XX based controllers having issues, I wonder if this boot parameter in /etc/default/grub would help with that...
```

GRUB_CMDLINE_LINUX="libata.force=15.00:sata,noncq,noncqtrim,rstonce,nohrst"

```

---

### Post by hjorden on 2024-05-20
> [COLOR=#000000]Check the PCIe slot that is being reported: 15:0.0.0[/COLOR]
Where do I see that? I only have that card and the graphics card in, so I guess it's that.

What does the GRUB line do?[COLOR=#000000][FONT=&quot]


[/FONT][/COLOR]You make it sound like I bought some extremely pricey piece of hardware :D

---

### Post by #&amp;thj^% on 2024-05-20
> **hjorden said:**
> Where do I see that? I only have that card and the graphics card in, so I guess it's that.
```
lspci
```
> **hjorden said:**
> 
What does the GRUB line do?[COLOR=#000000][FONT=&quot]
It's supposed to load the correct kernel parameters and functions for that hardware.

> **hjorden said:**
> 
[/FONT][/COLOR]You make it sound like I bought some extremely pricey piece of hardware :D

He was suggesting a better supported card is available.  I too feel this, your card is not the best option for Linux.

---

### Post by hjorden on 2024-05-20
Thanks!
That got me this:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 7
01:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset USB 3.1 XHCI Controller (rev 01)
01:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller (rev 01)
01:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge (rev 01)
02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
02:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
02:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
02:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
02:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9128 PCIe SATA 6 Gb/s RAID controller (rev 20)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
08:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
08:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function
0a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP
0a:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP
0a:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller
0a:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
0b:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
0c:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
```
Nothing about [COLOR=#000000][I]15:0.0.0

[/I][/COLOR]

> **1fallen said:**
> 
He was suggesting a better supported card is available.  I too feel this, your card is not the best option for Linux.
Ah, fair enough, had no idea. :)
To be honest, I don't think I gave it a thought at that time. :-k

---

### Post by #&amp;thj^% on 2024-05-20
> **hjorden said:**
> 
To be honest, I don't think I gave it a thought at that time. :-k
Most don't until the hardware does not work or work as expected....I always make sure every piece of hardware I buy "works on Linux"
Also your right this is your card in question:
```
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9128 PCIe SATA 6 Gb/s RAID controller (rev 20)
```
Try adding the grub suggestion and update-grub, and reboot to see if it helps or not.

EDIT: Have a look here: [https://www.marvell.com/support/downloads.html](https://www.marvell.com/support/downloads.html)
A driver maybe needed...But that is if your card is listed there, and I seen nothing for "88SE9128 PCIe SATA "

EDIT2: A little more thought makes me want you check your Bios to see if there is a setting to help with that card of yours...lol

---

### Post by hjorden on 2024-05-20
Yea, it been working fine for years now, just until the upgrade.
I've added the line, lets see what happens.

But it must somehow still be using some drivers, no? Since it can work for a period of time.

---

### Post by #&amp;thj^% on 2024-05-20
> **hjorden said:**
> 
But it must somehow still be using some drivers, no? Since it can work for a period of time.
That's what I would call *Not*"working as expected"

Please see if the grub changes help or not, keep us posted. :)
Also I added this edit in my above post^^^^
> EDIT2: A little more thought makes me want you check your Bios to see if there is a setting to help with that card of yours.
Last thought before I re-up on the bug report, we just don't have many kernel options on Noble ie:
```
rmadison linux-generic | grep noble
 linux-generic | 6.8.0-31.31            | noble           | amd64, arm64, armhf, ppc64el, s390x
 linux-generic | 6.8.0-31.31.1          | noble           | riscv64
 linux-generic | 6.8.0-32.32            | noble-proposed  | amd64, arm64, armhf, ppc64el, s390x

```
So I'm now leaning towards a bug found.....It has worked nicely until the upgrade to Noble.

---

### Post by hjorden on 2024-05-21
So the grub line didn't make a difference. Kernel panic again.

Tried writing Marvell about a driver.

I've actually haven't tried the BIOS update yet.

---

### Post by #&amp;thj^% on 2024-05-21
I thought as much, with the grub change....I'm not sure about the Bios Update myself.

This is one one of those damned if I do and damned if don't.

What makes the most logic now is to file the bug report.
I would also include this thread link, it has a ton of info we've already checked.

---

### Post by hjorden on 2024-05-24
Okay, so I tried removing the card.
But - kernel panic again! :(
[https://ibb.co/GF3ScQJ](https://ibb.co/GF3ScQJ)

Is there anything else I should try before the bug report since we have been investigating the wrong thing?

---

### Post by #&amp;thj^% on 2024-05-24
I still think it's a bug, will you now show this again please:
And It's important that the card is still not installed just yet.
```
 lshw -C cpu
```

---

### Post by hjorden on 2024-05-24
Keeping it removed for now. I wasn't actually in need of it anymore (:

```
  *-cpu
       description: CPU
       product: AMD Ryzen 5 3600X 6-Core Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 2f
       bus info: cpu@0
       version: 23.113.0
       serial: Unknown
       slot: AM4
       size: 2193MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm
sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr rdpru wbnoinvd arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif v_spec_ctrl umip rdpid overflow_recov succor smca sme sev sev_es cpufreq
       configuration: cores=6 enabledcores=6 microcode=141561875 threads=12 
```

---

### Post by #&amp;thj^% on 2024-05-24
Well that got rid of>>"*-processor UNCLAIMED" so we are not chasing our tails for that much.

Your going to be miles ahead filing the bug-report, they will know what else to try.
I still wonder about a Kernel 6.5 how well that would run, and for how long before another panic.

---

### Post by hjorden on 2024-05-24
Thanks for all the assistance :)

---

### Post by #&amp;thj^% on 2024-05-24
Do you want to try an older kernel?

EDIT: And did you remove the added parameter's from grub yet? (They are not needed now)

---

### Post by hjorden on 2024-05-24
If you recommend it, I can do that before filing a bug report, sure.

The one I upgraded from, it maybe became unresponsive every other month or something like that. But I never followed up on it since happened so rarely.

---

### Post by #&amp;thj^% on 2024-05-24
If it were me I'd try "6.5.11" and an easy way to handle it is here:[https://github.com/bkw777/mainline](https://github.com/bkw777/mainline)

If you have any troubles with that just ask I'll try to aide you.

---

### Post by hjorden on 2024-05-24
It says there was an error.

```
sudo mainline install 6.5.11mainline 1.4.10
Updating Kernels...
Downloading 6.5.11
Installing 6.5.11
Selecting previously unselected package linux-headers-6.5.11-060511.
(Reading database ... 142217 files and directories currently installed.)
Preparing to unpack .../linux-headers-6.5.11-060511_6.5.11-060511.202311151304_all.deb ...
Unpacking linux-headers-6.5.11-060511 (6.5.11-060511.202311151304) ...
Selecting previously unselected package linux-headers-6.5.11-060511-generic.
Preparing to unpack .../linux-headers-6.5.11-060511-generic_6.5.11-060511.202311151304_amd64.deb ...
Unpacking linux-headers-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
Selecting previously unselected package linux-image-unsigned-6.5.11-060511-generic.
Preparing to unpack .../linux-image-unsigned-6.5.11-060511-generic_6.5.11-060511.202311151304_amd64.deb ...
Unpacking linux-image-unsigned-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
Selecting previously unselected package linux-modules-6.5.11-060511-generic.
Preparing to unpack .../linux-modules-6.5.11-060511-generic_6.5.11-060511.202311151304_amd64.deb ...
Unpacking linux-modules-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
Setting up linux-headers-6.5.11-060511 (6.5.11-060511.202311151304) ...
dpkg: dependency problems prevent configuration of linux-headers-6.5.11-060511-generic:
 linux-headers-6.5.11-060511-generic depends on libc6 (>= 2.38); however:
  Version of libc6:amd64 on system is 2.35-0ubuntu3.7.


dpkg: error processing package linux-headers-6.5.11-060511-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-modules-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
Setting up linux-image-unsigned-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-107-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-107-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-6.5.11-060511-generic
I: /boot/initrd.img is now a symlink to initrd.img-6.5.11-060511-generic
Processing triggers for linux-image-unsigned-6.5.11-060511-generic (6.5.11-060511.202311151304) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.5.11-060511-generic
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-5.15.0-107-generic
Found kernel: /boot/vmlinuz-5.15.0-106-generic
Replacing config file /run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-6.5.11-060511-generic
Found kernel: /boot/vmlinuz-5.15.0-107-generic
Found kernel: /boot/vmlinuz-5.15.0-106-generic
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-curtin-settings.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.11-060511-generic
Found initrd image: /boot/initrd.img-6.5.11-060511-generic
Found linux image: /boot/vmlinuz-5.15.0-107-generic
Found initrd image: /boot/initrd.img-5.15.0-107-generic
Found linux image: /boot/vmlinuz-5.15.0-106-generic
Found initrd image: /boot/initrd.img-5.15.0-106-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Errors were encountered while processing:
 linux-headers-6.5.11-060511-generic
mainline: done
```

---

### Post by Doug S on 2024-05-25
Even with the header dependency issue the kernel should still run. Try it. Otherwise the kernel needs to be re-compiled using the version of Ubuntu it will run on.

---

### Post by #&amp;thj^% on 2024-05-25
+1 With Doug S
If your worried we can just remove it:
A good start is to see what you have now:
```
dpkg -l | awk '/linux-[^ ]+-[0-9]/ {print $2}'

```
We will go from here.

---

### Post by MAFoElffen on 2024-05-25
What I have not seen is a paste of the logs of what it was doing, and what happened just before the kernel panic... That might be useful.

Also, if you ran the UbuntuForums 'system-info' Script, that would tell us what you have hardware-wise, what the OS is using on that hardware, and how it was configured.

Without that information, we are fairly thin on information to go from.

---

### Post by #&amp;thj^% on 2024-05-25
> **MAFoElffen said:**
> What I have not seen is a paste of the logs of what it was doing, and what happened just before the kernel panic... That might be useful.

Also, if you ran the UbuntuForums 'system-info' Script, that would tell us what you have hardware-wise, what the OS is using on that hardware, and how it was configured.

Without that information, we are fairly thin on information to go from.

he did already: [https://paste.ubuntu.com/p/Yxwpz3KTkk/](https://paste.ubuntu.com/p/Yxwpz3KTkk/)

---

### Post by hjorden on 2024-05-25
> **1fallen said:**
> +1 With Doug S
If your worried we can just remove it:
A good start is to see what you have now:
```
dpkg -l | awk '/linux-[^ ]+-[0-9]/ {print $2}'

```
We will go from here.

I've rebooted and now running 6.5.11 
That command gave me


```
linux-headers-5.15.0-106-generic
linux-headers-5.15.0-107
linux-headers-5.15.0-107-generic
linux-headers-6.5.11-060511
linux-headers-6.5.11-060511-generic
linux-image-4.15.0-101-generic
linux-image-4.15.0-106-generic
linux-image-4.15.0-108-generic
linux-image-4.15.0-109-generic
linux-image-4.15.0-111-generic
linux-image-4.15.0-112-generic
linux-image-4.15.0-115-generic
linux-image-4.15.0-117-generic
linux-image-4.15.0-118-generic
linux-image-4.15.0-121-generic
linux-image-4.15.0-122-generic
linux-image-4.15.0-123-generic
linux-image-4.15.0-126-generic
linux-image-4.15.0-128-generic
linux-image-4.15.0-129-generic
linux-image-4.15.0-130-generic
linux-image-4.15.0-132-generic
linux-image-4.15.0-135-generic
linux-image-4.15.0-136-generic
linux-image-4.15.0-137-generic
linux-image-4.15.0-139-generic
linux-image-4.15.0-140-generic
linux-image-4.15.0-142-generic
linux-image-4.15.0-143-generic
linux-image-4.15.0-144-generic
linux-image-4.15.0-147-generic
linux-image-4.15.0-151-generic
linux-image-4.15.0-153-generic
linux-image-4.15.0-154-generic
linux-image-4.15.0-156-generic
linux-image-4.15.0-158-generic
linux-image-4.15.0-159-generic
linux-image-4.15.0-161-generic
linux-image-4.15.0-162-generic
linux-image-4.15.0-163-generic
linux-image-4.15.0-166-generic
linux-image-4.15.0-167-generic
linux-image-4.15.0-169-generic
linux-image-4.15.0-171-generic
linux-image-4.15.0-173-generic
linux-image-4.15.0-175-generic
linux-image-4.15.0-176-generic
linux-image-4.15.0-177-generic
linux-image-4.15.0-180-generic
linux-image-4.15.0-184-generic
linux-image-4.15.0-187-generic
linux-image-4.15.0-188-generic
linux-image-4.15.0-189-generic
linux-image-4.15.0-191-generic
linux-image-4.15.0-192-generic
linux-image-4.15.0-193-generic
linux-image-4.15.0-194-generic
linux-image-4.15.0-196-generic
linux-image-4.15.0-197-generic
linux-image-4.15.0-213-generic
linux-image-4.15.0-58-generic
linux-image-4.15.0-60-generic
linux-image-4.15.0-62-generic
linux-image-4.15.0-64-generic
linux-image-4.15.0-65-generic
linux-image-4.15.0-66-generic
linux-image-4.15.0-70-generic
linux-image-4.15.0-72-generic
linux-image-4.15.0-74-generic
linux-image-4.15.0-76-generic
linux-image-4.15.0-88-generic
linux-image-4.15.0-91-generic
linux-image-4.15.0-96-generic
linux-image-4.15.0-99-generic
linux-image-5.15.0-102-generic
linux-image-5.15.0-105-generic
linux-image-5.15.0-106-generic
linux-image-5.15.0-107-generic
linux-image-5.4.0-176-generic
linux-image-unsigned-6.5.11-060511-generic
linux-modules-4.15.0-101-generic
linux-modules-4.15.0-106-generic
linux-modules-4.15.0-108-generic
linux-modules-4.15.0-109-generic
linux-modules-4.15.0-111-generic
linux-modules-4.15.0-112-generic
linux-modules-4.15.0-115-generic
linux-modules-4.15.0-117-generic
linux-modules-4.15.0-118-generic
linux-modules-4.15.0-121-generic
linux-modules-4.15.0-122-generic
linux-modules-4.15.0-123-generic
linux-modules-4.15.0-126-generic
linux-modules-4.15.0-128-generic
linux-modules-4.15.0-129-generic
linux-modules-4.15.0-130-generic
linux-modules-4.15.0-132-generic
linux-modules-4.15.0-135-generic
linux-modules-4.15.0-136-generic
linux-modules-4.15.0-137-generic
linux-modules-4.15.0-139-generic
linux-modules-4.15.0-140-generic
linux-modules-4.15.0-142-generic
linux-modules-4.15.0-143-generic
linux-modules-4.15.0-144-generic
linux-modules-4.15.0-147-generic
linux-modules-4.15.0-151-generic
linux-modules-4.15.0-153-generic
linux-modules-4.15.0-154-generic
linux-modules-4.15.0-156-generic
linux-modules-4.15.0-158-generic
linux-modules-4.15.0-159-generic
linux-modules-4.15.0-161-generic
linux-modules-4.15.0-162-generic
linux-modules-4.15.0-163-generic
linux-modules-4.15.0-166-generic
linux-modules-4.15.0-167-generic
linux-modules-4.15.0-169-generic
linux-modules-4.15.0-171-generic
linux-modules-4.15.0-173-generic
linux-modules-4.15.0-175-generic
linux-modules-4.15.0-176-generic
linux-modules-4.15.0-177-generic
linux-modules-4.15.0-180-generic
linux-modules-4.15.0-184-generic
linux-modules-4.15.0-187-generic
linux-modules-4.15.0-188-generic
linux-modules-4.15.0-189-generic
linux-modules-4.15.0-191-generic
linux-modules-4.15.0-192-generic
linux-modules-4.15.0-193-generic
linux-modules-4.15.0-194-generic
linux-modules-4.15.0-196-generic
linux-modules-4.15.0-197-generic
linux-modules-4.15.0-213-generic
linux-modules-4.15.0-58-generic
linux-modules-4.15.0-60-generic
linux-modules-4.15.0-62-generic
linux-modules-4.15.0-64-generic
linux-modules-4.15.0-65-generic
linux-modules-4.15.0-66-generic
linux-modules-4.15.0-70-generic
linux-modules-4.15.0-72-generic
linux-modules-4.15.0-74-generic
linux-modules-4.15.0-76-generic
linux-modules-4.15.0-88-generic
linux-modules-4.15.0-91-generic
linux-modules-4.15.0-96-generic
linux-modules-4.15.0-99-generic
linux-modules-5.15.0-102-generic
linux-modules-5.15.0-105-generic
linux-modules-5.15.0-106-generic
linux-modules-5.15.0-107-generic
linux-modules-5.4.0-176-generic
linux-modules-6.5.11-060511-generic
linux-modules-extra-4.15.0-101-generic
linux-modules-extra-4.15.0-106-generic
linux-modules-extra-4.15.0-108-generic
linux-modules-extra-4.15.0-109-generic
linux-modules-extra-4.15.0-111-generic
linux-modules-extra-4.15.0-112-generic
linux-modules-extra-4.15.0-115-generic
linux-modules-extra-4.15.0-117-generic
linux-modules-extra-4.15.0-118-generic
linux-modules-extra-4.15.0-121-generic
linux-modules-extra-4.15.0-122-generic
linux-modules-extra-4.15.0-123-generic
linux-modules-extra-4.15.0-126-generic
linux-modules-extra-4.15.0-128-generic
linux-modules-extra-4.15.0-129-generic
linux-modules-extra-4.15.0-130-generic
linux-modules-extra-4.15.0-132-generic
linux-modules-extra-4.15.0-135-generic
linux-modules-extra-4.15.0-136-generic
linux-modules-extra-4.15.0-137-generic
linux-modules-extra-4.15.0-139-generic
linux-modules-extra-4.15.0-140-generic
linux-modules-extra-4.15.0-142-generic
linux-modules-extra-4.15.0-143-generic
linux-modules-extra-4.15.0-144-generic
linux-modules-extra-4.15.0-147-generic
linux-modules-extra-4.15.0-151-generic
linux-modules-extra-4.15.0-153-generic
linux-modules-extra-4.15.0-154-generic
linux-modules-extra-4.15.0-156-generic
linux-modules-extra-4.15.0-158-generic
linux-modules-extra-4.15.0-159-generic
linux-modules-extra-4.15.0-161-generic
linux-modules-extra-4.15.0-162-generic
linux-modules-extra-4.15.0-163-generic
linux-modules-extra-4.15.0-166-generic
linux-modules-extra-4.15.0-167-generic
linux-modules-extra-4.15.0-169-generic
linux-modules-extra-4.15.0-171-generic
linux-modules-extra-4.15.0-173-generic
linux-modules-extra-4.15.0-175-generic
linux-modules-extra-4.15.0-176-generic
linux-modules-extra-4.15.0-177-generic
linux-modules-extra-4.15.0-180-generic
linux-modules-extra-4.15.0-184-generic
linux-modules-extra-4.15.0-187-generic
linux-modules-extra-4.15.0-188-generic
linux-modules-extra-4.15.0-189-generic
linux-modules-extra-4.15.0-191-generic
linux-modules-extra-4.15.0-192-generic
linux-modules-extra-4.15.0-193-generic
linux-modules-extra-4.15.0-194-generic
linux-modules-extra-4.15.0-196-generic
linux-modules-extra-4.15.0-197-generic
linux-modules-extra-4.15.0-213-generic
linux-modules-extra-4.15.0-58-generic
linux-modules-extra-4.15.0-60-generic
linux-modules-extra-4.15.0-62-generic
linux-modules-extra-4.15.0-64-generic
linux-modules-extra-4.15.0-65-generic
linux-modules-extra-4.15.0-66-generic
linux-modules-extra-4.15.0-70-generic
linux-modules-extra-4.15.0-72-generic
linux-modules-extra-4.15.0-74-generic
linux-modules-extra-4.15.0-76-generic
linux-modules-extra-4.15.0-88-generic
linux-modules-extra-4.15.0-91-generic
linux-modules-extra-4.15.0-96-generic
linux-modules-extra-4.15.0-99-generic
linux-modules-extra-5.15.0-102-generic
linux-modules-extra-5.15.0-105-generic
linux-modules-extra-5.15.0-106-generic
linux-modules-extra-5.15.0-107-generic
linux-modules-extra-5.4.0-176-generic
```

---

### Post by #&amp;thj^% on 2024-05-25
That command was a from the hip, and not what I wanted, My Bad :(
This would be better for me:
```
dpkg -l | grep "linux\-[a-z]*\-"
```

But no worries on how fast you reply, I'm more interested if it panics again.

---

### Post by hjorden on 2024-05-26
Just got a kernel panic again :(


Heres the output of ```
 dpkg -l | grep "linux\-[a-z]*\-"
```
```

ii  linux-headers-5.15.0-106                   5.15.0-106.116                          all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-106-generic           5.15.0-106.116                          amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-5.15.0-107                   5.15.0-107.117                          all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-107-generic           5.15.0-107.117                          amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-6.5.11-060511                6.5.11-060511.202311151304              all          Header files related to Linux kernel version 6.5.11
iU  linux-headers-6.5.11-060511-generic        6.5.11-060511.202311151304              amd64        Linux kernel headers for version 6.5.11 on 64 bit x86 SMP
ii  linux-headers-generic                      5.15.0.107.107                          amd64        Generic Linux kernel headers
rc  linux-image-4.15.0-101-generic             4.15.0-101.102                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-106-generic             4.15.0-106.107                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-108-generic             4.15.0-108.109                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-109-generic             4.15.0-109.110                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-111-generic             4.15.0-111.112                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-112-generic             4.15.0-112.113                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-115-generic             4.15.0-115.116                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-117-generic             4.15.0-117.118                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-118-generic             4.15.0-118.119                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-121-generic             4.15.0-121.123                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-122-generic             4.15.0-122.124                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-123-generic             4.15.0-123.126                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-126-generic             4.15.0-126.129                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-128-generic             4.15.0-128.131                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-129-generic             4.15.0-129.132                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-130-generic             4.15.0-130.134                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-132-generic             4.15.0-132.136                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-135-generic             4.15.0-135.139                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-136-generic             4.15.0-136.140                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-137-generic             4.15.0-137.141                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-139-generic             4.15.0-139.143                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-140-generic             4.15.0-140.144                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-142-generic             4.15.0-142.146                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-143-generic             4.15.0-143.147                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-144-generic             4.15.0-144.148                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-147-generic             4.15.0-147.151                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-151-generic             4.15.0-151.157                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-153-generic             4.15.0-153.160                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-154-generic             4.15.0-154.161                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-156-generic             4.15.0-156.163                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-158-generic             4.15.0-158.166                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-159-generic             4.15.0-159.167                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-161-generic             4.15.0-161.169                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-162-generic             4.15.0-162.170                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-163-generic             4.15.0-163.171                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-166-generic             4.15.0-166.174                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-167-generic             4.15.0-167.175                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-169-generic             4.15.0-169.177                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-171-generic             4.15.0-171.180                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-173-generic             4.15.0-173.182                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-175-generic             4.15.0-175.184                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-176-generic             4.15.0-176.185                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-177-generic             4.15.0-177.186                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-180-generic             4.15.0-180.189                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-184-generic             4.15.0-184.194                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-187-generic             4.15.0-187.198                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-188-generic             4.15.0-188.199                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-189-generic             4.15.0-189.200                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-191-generic             4.15.0-191.202                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-192-generic             4.15.0-192.203                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-193-generic             4.15.0-193.204                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-194-generic             4.15.0-194.205                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-196-generic             4.15.0-196.207                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-197-generic             4.15.0-197.208                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-213-generic             4.15.0-213.224                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-58-generic              4.15.0-58.64                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-60-generic              4.15.0-60.67                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-62-generic              4.15.0-62.69                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-64-generic              4.15.0-64.73                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-65-generic              4.15.0-65.74                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-66-generic              4.15.0-66.75                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-70-generic              4.15.0-70.79                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-72-generic              4.15.0-72.81                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-74-generic              4.15.0-74.84                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-76-generic              4.15.0-76.86                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-88-generic              4.15.0-88.88                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-91-generic              4.15.0-91.92                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-96-generic              4.15.0-96.97                            amd64        Signed kernel image generic
rc  linux-image-4.15.0-99-generic              4.15.0-99.100                           amd64        Signed kernel image generic
rc  linux-image-5.15.0-102-generic             5.15.0-102.112                          amd64        Signed kernel image generic
rc  linux-image-5.15.0-105-generic             5.15.0-105.115                          amd64        Signed kernel image generic
ii  linux-image-5.15.0-106-generic             5.15.0-106.116                          amd64        Signed kernel image generic
ii  linux-image-5.15.0-107-generic             5.15.0-107.117                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-176-generic              5.4.0-176.196                           amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.107.107                          amd64        Generic Linux kernel image
ii  linux-image-unsigned-6.5.11-060511-generic 6.5.11-060511.202311151304              amd64        Linux kernel image for version 6.5.11 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                       5.15.0-107.117                          amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-101-generic           4.15.0-101.102                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-106-generic           4.15.0-106.107                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-108-generic           4.15.0-108.109                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-109-generic           4.15.0-109.110                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-111-generic           4.15.0-111.112                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-112-generic           4.15.0-112.113                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-115-generic           4.15.0-115.116                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-117-generic           4.15.0-117.118                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-118-generic           4.15.0-118.119                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-121-generic           4.15.0-121.123                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-122-generic           4.15.0-122.124                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-123-generic           4.15.0-123.126                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-126-generic           4.15.0-126.129                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-128-generic           4.15.0-128.131                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-129-generic           4.15.0-129.132                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-130-generic           4.15.0-130.134                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-132-generic           4.15.0-132.136                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-135-generic           4.15.0-135.139                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-136-generic           4.15.0-136.140                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-137-generic           4.15.0-137.141                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-139-generic           4.15.0-139.143                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-140-generic           4.15.0-140.144                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-142-generic           4.15.0-142.146                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-143-generic           4.15.0-143.147                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-144-generic           4.15.0-144.148                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-147-generic           4.15.0-147.151                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-151-generic           4.15.0-151.157                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-153-generic           4.15.0-153.160                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-154-generic           4.15.0-154.161                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-156-generic           4.15.0-156.163                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-158-generic           4.15.0-158.166                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-159-generic           4.15.0-159.167                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-161-generic           4.15.0-161.169                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-162-generic           4.15.0-162.170                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-163-generic           4.15.0-163.171                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-166-generic           4.15.0-166.174                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-167-generic           4.15.0-167.175                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-169-generic           4.15.0-169.177                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-171-generic           4.15.0-171.180                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-173-generic           4.15.0-173.182                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-175-generic           4.15.0-175.184                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-176-generic           4.15.0-176.185                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-177-generic           4.15.0-177.186                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-180-generic           4.15.0-180.189                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-184-generic           4.15.0-184.194                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-187-generic           4.15.0-187.198                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-188-generic           4.15.0-188.199                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-189-generic           4.15.0-189.200                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-191-generic           4.15.0-191.202                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-192-generic           4.15.0-192.203                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-193-generic           4.15.0-193.204                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-194-generic           4.15.0-194.205                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-196-generic           4.15.0-196.207                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-197-generic           4.15.0-197.208                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-213-generic           4.15.0-213.224                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-58-generic            4.15.0-58.64                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-60-generic            4.15.0-60.67                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-62-generic            4.15.0-62.69                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-64-generic            4.15.0-64.73                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-65-generic            4.15.0-65.74                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-66-generic            4.15.0-66.75                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-70-generic            4.15.0-70.79                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-72-generic            4.15.0-72.81                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-74-generic            4.15.0-74.84                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-76-generic            4.15.0-76.86                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-88-generic            4.15.0-88.88                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-91-generic            4.15.0-91.92                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-96-generic            4.15.0-96.97                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-99-generic            4.15.0-99.100                           amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-102-generic           5.15.0-102.112                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-105-generic           5.15.0-105.115                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-106-generic           5.15.0-106.116                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-107-generic           5.15.0-107.117                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-176-generic            5.4.0-176.196                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-6.5.11-060511-generic        6.5.11-060511.202311151304              amd64        Linux kernel extra modules for version 6.5.11 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-101-generic     4.15.0-101.102                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-106-generic     4.15.0-106.107                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-108-generic     4.15.0-108.109                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-109-generic     4.15.0-109.110                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-111-generic     4.15.0-111.112                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-112-generic     4.15.0-112.113                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-115-generic     4.15.0-115.116                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-117-generic     4.15.0-117.118                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-118-generic     4.15.0-118.119                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-121-generic     4.15.0-121.123                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-122-generic     4.15.0-122.124                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-123-generic     4.15.0-123.126                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-126-generic     4.15.0-126.129                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-128-generic     4.15.0-128.131                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-129-generic     4.15.0-129.132                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-130-generic     4.15.0-130.134                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-132-generic     4.15.0-132.136                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-135-generic     4.15.0-135.139                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-136-generic     4.15.0-136.140                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-137-generic     4.15.0-137.141                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-139-generic     4.15.0-139.143                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-140-generic     4.15.0-140.144                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-142-generic     4.15.0-142.146                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-143-generic     4.15.0-143.147                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-144-generic     4.15.0-144.148                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-147-generic     4.15.0-147.151                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-151-generic     4.15.0-151.157                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-153-generic     4.15.0-153.160                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-154-generic     4.15.0-154.161                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-156-generic     4.15.0-156.163                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-158-generic     4.15.0-158.166                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-159-generic     4.15.0-159.167                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-161-generic     4.15.0-161.169                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-162-generic     4.15.0-162.170                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-163-generic     4.15.0-163.171                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-166-generic     4.15.0-166.174                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-167-generic     4.15.0-167.175                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-169-generic     4.15.0-169.177                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-171-generic     4.15.0-171.180                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-173-generic     4.15.0-173.182                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-175-generic     4.15.0-175.184                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-176-generic     4.15.0-176.185                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-177-generic     4.15.0-177.186                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-180-generic     4.15.0-180.189                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-184-generic     4.15.0-184.194                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-187-generic     4.15.0-187.198                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-188-generic     4.15.0-188.199                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-189-generic     4.15.0-189.200                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-191-generic     4.15.0-191.202                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-192-generic     4.15.0-192.203                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-193-generic     4.15.0-193.204                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-194-generic     4.15.0-194.205                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-196-generic     4.15.0-196.207                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-197-generic     4.15.0-197.208                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-213-generic     4.15.0-213.224                          amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-58-generic      4.15.0-58.64                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-60-generic      4.15.0-60.67                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-62-generic      4.15.0-62.69                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-64-generic      4.15.0-64.73                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-65-generic      4.15.0-65.74                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-66-generic      4.15.0-66.75                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-70-generic      4.15.0-70.79                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-72-generic      4.15.0-72.81                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-74-generic      4.15.0-74.84                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-76-generic      4.15.0-76.86                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-88-generic      4.15.0-88.88                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-91-generic      4.15.0-91.92                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-96-generic      4.15.0-96.97                            amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-99-generic      4.15.0-99.100                           amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-102-generic     5.15.0-102.112                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-105-generic     5.15.0-105.115                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-106-generic     5.15.0-106.116                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-107-generic     5.15.0-107.117                          amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-176-generic      5.4.0-176.196                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
```

---

### Post by #&amp;thj^% on 2024-05-26
By Golly I'm just stumped now. I see a lot of leftover .conf from past kernels.

I have nothing concrete to suggest currently.

Maybe Doug S or MAFoElffen might have something to add.

---

### Post by hjorden on 2024-05-26
Damn :/
What was it supposed to show?

I tried following [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) to make a bug report. 
But I can only find info on how to file a bug report against a package. Does that make sense in this case?

---

### Post by #&amp;thj^% on 2024-05-26
> **hjorden said:**
>  Does that make sense in this case?

Not really, we don't have a clue why or what package is giving you the panic.

---

### Post by hjorden on 2024-05-26
> **1fallen said:**
> Not really, we don't have a clue why or what package is giving you the panic.
Do you know how to file a report without a package?
Am I blind or doesn't it give that info &#128517;

---

### Post by #&amp;thj^% on 2024-05-26
It has to have a package-name to file any bug..

Causes of Kernel Panic

There are several causes, but most common are listed below:
[list]
    [*]Defective or Incompatible RAM is the most common and frequent cause of Kernel Panic.
    [*]Obsolete, Incompatible or Corrupted Kernel Extensions
    [*]Obsolete, Incompatible or Corrupted Kernel Drivers.
    [*]Hard disk corruption or issues such as bad sectors or directory corruption can also lead to kernel panic.
    [*]Insufficient RAM or Hard disk space
    [*]Defective hardware, badly written programs or hardware failures can also lead to kernel Panic.[/list]

This is also important to note that only modules that are located within the kernel space can cause kernel panic. lsmod command can be run to get a list of dynamically loaded modules.

To troubleshoot kernel panic, check /var/log/messages. Sometimes all of the information might be logged there or while sometimes nothing related to kernel panic might be logged there.

---

### Post by hjorden on 2024-07-07
Could i just downgrade the kennel to the one used before?

---

### Post by hjorden on 2024-07-11
The kernel panic is happening more and more frequent.
Not entirely sure, but before where it could go over a day, it seems like its only alive for couple of hours.

Could that give a hint for something else to check?

---

### Post by #&amp;thj^% on 2024-07-11
> **hjorden said:**
> 
Could that give a hint for something else to check?
Nope.

Which kernel is this happening on, and I thought you was booting to an older kernel....is this still the case?

---

### Post by hjorden on 2024-07-13
Happens both on the 6.x something and the 5.x something.

Is there nothing I can do, like go back to the old kernel (no longer installed) and Ubuntu 18, or whichever I came from.

---

### Post by #&amp;thj^% on 2024-07-13
You keep asking if anything can be done, Doug S and i have kind of given up on you.

We keep asking for info needed but nothing comes back.

I'm pretty sure it's either a Hardware issue, or your system is very degraded or corrupt.
At this point I would if I were you, Fresh Clean install, just to check against a degraded or corrupt system.

Sorry

---

### Post by hjorden on 2024-07-13
Yea sorry.

Hard to accept I had a working system, wanting to upgrade and now it feels like a huge brick.

Thanks for all the help!
Much appreciated.

---

### Post by Doug S on 2024-07-14
I've re-read this thread. I don't have anything to add. I worry about using tainted kernels and out of tree modules.

It is an extreme long shot, but one thing I do with these type of issues is reduce the maximum CPU frequency so as to increase timing margins.

---

