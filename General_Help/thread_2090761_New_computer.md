---
title: "New computer"
date: 2012-12-03
forum: General Help
---

### Post by northwestern on 2012-12-03
I have just replaced my broken HP DV5 laptop with a new Samsung NP350V5C-A08.
I have always run ubuntu from an external USB hardrive, the boot order on my HP was :
a) Internal read/write disc player.
b) USB ports (for external drive).
c) Internal hard drive.

My Samsung ignores the Ubuntu disk and boots straight into Windows 8, I have gone into BIOS to look at the boot order but it is completely different to the HP one leaving me puzzled.

I am missing using Ubuntu and any help to download the program onto my external drive would be welcome.
Regards
Northwestern

---

### Post by sandyd on 2012-12-03
> **northwestern said:**
> I have just replaced my broken HP DV5 laptop with a new Samsung NP350V5C-A08.
I have always run ubuntu from an external USB hardrive, the boot order on my HP was :
a) Internal read/write disc player.
b) USB ports (for external drive).
c) Internal hard drive.

My Samsung ignores the Ubuntu disk and boots straight into Windows 8, I have gone into BIOS to look at the boot order but it is completely different to the HP one leaving me puzzled.

I am missing using Ubuntu and any help to download the program onto my external drive would be welcome.
Regards
Northwestern

Have you tried switching the boot order to boot from USB/CD first?

If not, what is your BIOS's current boot order?

---

### Post by coldraven on 2012-12-03
Two things: 
On my laptop if I press F9 as it boots it will take me to a boot order menu. This saves having to press F10 to go into the BIOS settings and change the order.

If I try to boot from USB HDD and I have left a SD card in the card reader it won't boot.
I guess it only looks once, finds a non-bootable medium and then stops looking.

My laptop is a Compaq but your one might have a similar function.

---

### Post by oldfred on 2012-12-03
If a new Windows 8 system pre-installed it will be UEFI with secure boot. 

Ubuntu 12.10 has the new grub2 2.00 that supports secure boot. 

But you may be able to turn secure boot off. Not sure if you then can directly boot external if still in BIOS mode or not. 

Not sure if similar system or UEFI implementation or not:
       Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by northwestern on 2012-12-04
Thank you for your replies.
The boot order in the Samsung is completely different from the HP.
At the moment the SECURE BOOT is enabled..

The boot options are:
Boot Option #1 [Windows Boot manager].
Boot Option #2 [UEFI].

Picking any of those options gives me a choice of PO Hitachi Drive or Delete.

I hope this helps.
Regards northwestern

---

### Post by 2F4U on 2012-12-04
Not sure if this helps. This Wiki article describes how to get Ubuntu installed with UEFI and secure boot.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The article suggests that you may have to temporarily disable secure boot.

---

