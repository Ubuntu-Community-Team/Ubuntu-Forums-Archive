---
title: "gigabyte skylake motherboard, how to update intel microcode?"
date: 2016-05-18
forum: General Help
---

### Post by unknown14 on 2016-05-18
Hi,

As title, a gigabyte motherboard, as I was totally unable to get win7 onto the MB, I have installed Ubuntu, working quite well, but the skylake micro is as below:
vendor_id    : GenuineIntel
cpu family    : 6
model        : 94
model name    : Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz
stepping    : 3
microcode    : 0x6a
cpu MHz        : 872.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp
bugs        :
bogomips    : 6383.90
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


So the microcode is out of date and gigabyte ONLY provides a windows .exe file to update with, grrr, 
So any tips or hints or other ways to update the bios?

---

### Post by cbraxton on 2016-05-18
If you look in "additional drivers" you should see an option to use proprietary Intel microcode firmware.

---

### Post by oldfred on 2016-05-18
I am using this system without any obvious issues.
 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ) 

Since an UEFI system, you would want to convert the Windows 7 installer to UEFI. The DVD is BIOS only, and you have to copy to a flash drive and move the efi boot files into /EFI/Boot and rename a file to bootx64.efi. 

The next kernel or two will have more updates for Intel and other improvements, some Haswell & some Skylake.
[http://www.phoronix.com/scan.php?page=article&item=linux-46-features&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-46-features&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-Early-Look](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.7-Early-Look)

---

### Post by unknown14 on 2016-05-19
Hi,

Well win 7 kept blue screening during the initial install process, nlite etc never got me past that. It is a UEFI boot for sure, I used a FAT32 USB prepared with RUFUS to install first SUSE Leap42 then Ubuntu 16.04.

"Since an UEFI system, you would want to convert the Windows 7 installer  to UEFI. The DVD is BIOS only, and you have to copy to a flash drive and  move the efi boot files into /EFI/Boot and rename a file to  bootx64.efi." I am not sure what you mean here, do you mean I can run the exe file at the bios screen?

To Cbraxton, sorry to sound daft, but where do I look for "additional drivers"?

---

### Post by oldfred on 2016-05-19
System will install all the normal drivers.

If video or Wireless proprietary drivers required, Use System Settings, Software & Updates. This is for Ubuntu, not sure where on other flavors.

---

### Post by Linuxisfast on 2016-05-19
Under 16.04 Intel microcode is installed during fresh install once the script senses a Intel CPU, both my older Sandybridge X-220 ThinkPad and newer i7 Haswell refresh where microcode is installed right out of box.

---

### Post by unknown14 on 2016-05-22
Hi,

The problem is that other skylake and linux threads on the  web say that the microcode should be at 75 or greater, mine is at ox6A,  so is out of date, the intel graphics video was unusable on suse  leap42.1, so that had to be abandoned.

I know that gigabyte have  provided updated firmware images, but their installer tool is windows  only, so currently of no use to me as win7 was bluescreening at one of  the intermediate image states every time I tried.

so the original  question still stands I also have an i5-6500 skylake processor, but  would also like the dual monitor capability to work, currently the extra  screen is not recognised.

---

### Post by mc4man on 2016-05-22
> **unknown14 said:**
> Hi,

The problem is that other skylake and linux threads on the  web say that the microcode should be at 75 or greater, mine is at ox6A,  so is out of date, the intel graphics video was unusable on suse  leap42.1, so that had to be abandoned.


Isn't 106 greater than 75?

---

### Post by unknown14 on 2016-05-23
> **mc4man said:**
> Isn't 106 greater than 75?
I believe it is ox75 not decimal 75, as this page shows:
[http://www.anandtech.com/show/10021/skylake-overclocking-regular-cpu-bclk-overclocking-is-being-removed](http://www.anandtech.com/show/10021/skylake-overclocking-regular-cpu-bclk-overclocking-is-being-removed)

---

### Post by buzzingrobot on 2016-05-23
Intel has two archives of Linux firmware for Skylakes here: [https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

Extract the archives and execute the install script in each using sudo.

Firmware for this lives in /lib/firmware/i915.  Check there first to see if the most current is not already there.

CAVEAT:  Installing these makes changes in the initramfs used by the boot process.  The script does make a backup. 

I've installed these a number of times without a problem. Still, be careful.

---

