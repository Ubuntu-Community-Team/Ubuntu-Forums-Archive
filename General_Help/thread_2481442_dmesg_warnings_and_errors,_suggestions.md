---
title: "dmesg warnings and errors, suggestions?"
date: 2022-11-13
forum: General Help
---

### Post by whizatit on 2022-11-13
Hello and thank you to any and all for your help! I Have a ASUS Zenith Extreme v2.0, 64Gb ram,1Tb Samsung PRO SATA drive OS lives here three Samgung EVO Pro 512Gb NVME drives MDADM raid 0 games live here, three spinnup 4TB HDD's MDADM raid 0 misc lives here, Nvidia 1070 Turbo 8Gb ram. Anything else needed lemmie know!
I have several boot warnings and a couple errors i would like input on as to if to ignore some (im sure there are a few), and fix others if possible! 

Here are the warnings...

```
[    0.032000] tsc: Unable to calibrate against PIT
[    0.334173] AMD-Vi: [Firmware Warn]: EFR mismatch. Use IVHD EFR (0xf77ef22294ada : 0x400f77ef22294ada).
[    0.334202] AMD-Vi: [Firmware Warn]: EFR mismatch. Use IVHD EFR (0xf77ef22294ada : 0x400f77ef22294ada).
[    0.416271] device-mapper: core: CONFIG_IMA_DISABLE_HTABLE is disabled. Duplicate IMA measurements will not be recorded in the IMA log.
[    0.416362] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.416365] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.416367] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.416370] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.416372] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.416374] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.416376] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.416378] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.416381] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.024535] acpi PNP0C14:02: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:01)
[    1.071899] nvme1n1: p1 size 1000215216 extends beyond EOD, truncated
[    1.072113] nvme2n1: p1 size 1000215216 extends beyond EOD, 
[    1.072808] nvme0n1: p1 size 1000215216 extends beyond EOD, 
[    1.073489] truncated
[    1.076297] truncated
[    2.028865] ata2.00: ATA Identify Device Log not supported
[    2.033373] ata2.00: ATA Identify Device Log not supported
[    5.552188] ata8: failed to resume link (SControl 0)
[   10.962343] nvidia: loading out-of-tree module taints kernel.
[   10.962356] nvidia: module license 'NVIDIA' taints kernel.
[   10.962358] Disabling lock debugging due to kernel taint
[   11.209175] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  515.65.01  Wed Jul 20 14:00:58 UTC 2022
[   13.432391] nvidia_uvm: module uses symbols from proprietary module nvidia, inheriting taint.
[   16.372221] kauditd_printk_skb: 65 callbacks suppressed
[   18.970355] exFAT-fs (sdd1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   21.864501] kauditd_printk_skb: 20 callbacks suppressed
[  480.986374] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[  702.992992] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[  973.001907] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[ 1123.001043] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[ 1153.001170] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[ 1183.001716] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[ 1213.000534] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
[ 1555.004231] ath10k_pci 0000:03:00.0: invalid vht params rate 960 100kbps nss 1 mcs 9
```

And here are the errors...
[    3.144194] usb 1-6.1: device descriptor read/64, error -32     <<<< THIS I KNOW TO IGNORE!!! However, would like to know the error code list!


[   22.236652] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00004300] Failed to grab modeset ownership


Current Ubuntu 22.04 all updates and Nvidia driver.

Any Tips and help appreciated!

Main reason im asking here is because A) Its Ubuntu B) All other refrences are years old or pertain to different distros.

All works as intended no issues or hangs etc in the OS just wondering if there are fixes, hacks etc for these and what to and not to worry about!

---

### Post by whizatit on 2022-11-29
I really adore the "support" of this open source community, been waiting 2 weeks for any reply :(

---

### Post by #&amp;thj^% on 2022-11-29
We all are volunteer's here and your post was first added 2 weeks ago, easily sinks to the bottom of the pile, you can refresh or bump
your request @ a 12 hour interval to keep you in site of someone that could help you. ;)
But a first guess here>> is bad USB firmware .

---

### Post by QIII on 2022-11-29
Your post is also in a chat area, not a support area, so it may have been overlooked.

There is presently some wonkiness with the forum software, but I will attempt to move this to a support area later.

---

### Post by QIII on 2022-11-29
Thread moved to General Help

---

### Post by TheFu on 2022-11-30
> **whizatit said:**
> 
Any Tips and help appreciated!


Nothing specific to your question, but using RAID0 on spinning HDDs is crazy.  Expect to lose all the data on all drives when 1 fails.  You've been warned.

Also, don't use exFAT unless absolutely necessary. Necessary would mean that the device will be directly connected to other hardware or OS for access.  For Linux-only access, exFAT should be avoided. Use f2fs for USB flash storage and ext4 or zfs for permanent Linux storage on HDDs or and SSD.  f2fs keeps the write counts down, since it isn't journaled, but for most of our storage needs, we really, really, really, want journaled file systems.  Us old-guys remember before journaled file systems were common and how painful little issues were to resolve.

SSDs have the same risks, but are much more likely not to have issues, unless you self-inflict them  by hitting the endurance limits in the specification.
BTW, using the SATA SSD for the OS and not an NVMe SSD is a 4x performance hit.  NVMe is 4x faster than most SATA SSDs.

BTW, in the posted output, I'm seeing only informational messages, not warnings or errors. Perhaps I'm just not seeing it, but those are usually CLEARLY marked with WARNING or ERROR in the line.

The subject of this thread wasn't sufficient to grab my attention and like many people in my country a few weeks ago, we were busy preparing for a big multi-day national holiday.

---

### Post by oldfred on 2022-11-30
Have  you updated UEFI firmware and all the SSD/NVMe drive's firmware?

Do you have a duplicate GUID?

Did you install nVidia from Ubuntu repository? And is it correct version?

Did you run the suggested fsck on your exFAT partition? Not sure if Ubuntu has a tool for that, as mainly a Microsoft format.

---

### Post by #&amp;thj^% on 2022-11-30
> **TheFu said:**
> Nothing specific to your question, but using RAID0 on spinning HDDs is crazy.  Expect to lose all the data on all drives when 1 fails.  You've been warned.
 the line.

The subject of this thread wasn't sufficient to grab my attention and like many people in my country a few weeks ago, we were busy preparing for a big multi-day national holiday.
+1 to all the above
I'm still guessing on the bad firmware, and if Nvidia is loaded correctly, I may be wrong but that tells me of Impending Drive failure and again OP has been warned. 
I hate seeing this " device descriptor read/64, error -32" so just In my experience with computing that has never never had a happy ending.
TheFu is super knowledgeable on these matters. Good Luck though.

---

### Post by TheFu on 2022-11-30
> **1fallen said:**
> +1 to all the above
I'm still guessing on the bad firmware, and if Nvidia is loaded correctly, I may be wrong but that tells me of Impending Drive failure and again OP has been warned. 
I hate seeing this " device descriptor read/64, error -32" so just In my experience with computing that has never never had a happy ending.
TheFu is super knowledgeable on these matters. Good Luck though.

You are too kind, as usual.

For drive stuff, I use smartctl and NVMe SSDs have terrible SMART information, IME.  I'd run a short test on each storage device to see where it is today and lookup what I didn't understand already.  I have an NVMe SSD that reports issues at each boot. It is relatively new top consumer device and very fast. It has the latest available firmware and was actually shipped with it (which surprised me).

So ... when it comes to NVMe issues, doubt that I know much more than anyone else.  Of course, when it comes to SATA HDDs, I'm willing to look stupid, since I've seen lots and lots of failures with those over the decades.   I've been fortunate with SATA-SSD failures, in that they provided plenty of advanced warning, but I've heard of many more situations where they just stopped working completely and never worked again.

Check the SMART data for your storage if you want to know what is the best guess at what is happening.  However, SMART isn't perfect. A huge HDD user tracks drive failures and their testing of hundreds of thousands of HDDs says that only 78% of the time does the data available in SMART provide any hint BEFORE a drive fails.  So, 22% of the time, there's no warning at all.

What can we do with all this information?  Know that backups are the only way to manage risks for any sort of storage.  If you have backups, a drive failure is an inconvenience, not the end of the world.  If the system/data aren't worth having backups, then there will be very little sympathy from me when everything is lost. It may seem harsh, but all storage fails and we don't get to pick when that will happen. That's the real world.

---

### Post by MAFoElffen on 2022-11-30
My +1 is to ask which AMD Ryzen processor is it using?

---

