---
title: "dual boot"
date: 2014-12-10
forum: General Help
---

### Post by markdavis on 2014-12-10
hi ive installed windows first and then ubuntu 14 on my new computer / but i dont get the option for dual boot , can i do this now after ive installed both . thanks in advance

---

### Post by Gordonbp531 on 2014-12-10
1. What version of Windows?

2. What make and model of computer, and is it UEFI and secure boot enabled?

3. If it is UEFI where did you install the GRUB bootloader?

---

### Post by markdavis on 2014-12-10
hi thank for the reply . its windows 7 on a zoostorm desktop amd a8-7600 secure boot is not active / not sure about grub , i installed windows on its own partition along with a second for d drive sda 5 is swap and sda 6 is ubuntu hope this is of some use to you as im still learning thanks / mark

---

### Post by markdavis on 2014-12-10
ps yes it is uefi

---

### Post by oldfred on 2014-12-10
Even if hardware is UEFI, most Windows 7 installs are BIOS with MBR partitioning. You can convert a Windows 7 flash drive to UEFI install.
Windows 7 does not support secure boot either.

Best to see all details, post link to summary report, you can install this into a working Ubuntu install or the live installer if you cannot boot:

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

