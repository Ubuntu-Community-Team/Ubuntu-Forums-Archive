---
title: "Going to dualboot Windows 8.1 &amp; Trusty Tahr"
date: 2014-10-09
forum: General Help
---

### Post by sports fan Matt on 2014-10-09
Besides UEFI, (Which I do not think my Toshiba L875-S7208 has because I do not see an option to disable it) are there any more red flags I need to look out for before attempting the dualboot process?  

I'm retiring my old HP DV 4000 which had Precise on it.

Thanks,
Matt

---

### Post by sandyd on 2014-10-09
> **sports fan Matt said:**
> Besides UEFI, (Which I do not think my Toshiba L875-S7208 has because I do not see an option to disable it) are there any more red flags I need to look out for before attempting the dualboot process?  

I'm retiring my old HP DV 4000 which had Precise on it.

Thanks,
Matt

It normally shows up as Secure Boot, not UEFI in the BIOS - however Ubuntu should work fine with Secure Boot on provided you are using 14.04.

---

### Post by sports fan Matt on 2014-10-09
Had forgotten about that.  I was planning on upgrading to 14.04 as this disk has precise on it.

---

### Post by oldfred on 2014-10-09
Almost all UEFI systems still have the old BIOS mode which may be called CSM or legacy boot.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But if Windows is UEFI, you really want Ubuntu in UEFI boot mode. And UEFI is a lot different than the old BIOS. Often UEFI/BIOS settings required particularly turning off Windows 8 fast boot and usually secure boot. And Windows 8.1 likes to reset itself as default, so work arounds usually required.

      
 Windows 10 Dual boot on Toshiba works - sudodus
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869](http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869)

 Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

      
 [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)

See also links below if you need more info:

---

### Post by sports fan Matt on 2014-10-09
Oldfred, thank you. I have divided 320 GB equally on both my Ubuntu and W8 partitions (although I don't think I will need the whole 320 GB's for Ubuntu, I only want these OS's on my host system.

---

