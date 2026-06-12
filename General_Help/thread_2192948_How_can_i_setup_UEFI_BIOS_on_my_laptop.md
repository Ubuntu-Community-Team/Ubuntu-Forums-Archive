---
title: "How can i setup UEFI BIOS on my laptop"
date: 2013-12-10
forum: General Help
---

### Post by penuel1310 on 2013-12-10
Hi everyone, can someone please tell me if its possible to setup UEFI on top of my current BIOS or replace BIOS and setup UEFI?
can i actually install UEFI on my laptop? i'm confused.... someone please explain.

Thankyou...

---

### Post by oldfred on 2013-12-10
You only can have UEFI if vendor originally installed it as part of computer. But almost all UEFI have a CSM/BIOS mode.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
All Windows 8 pre-installed systems are UEFI with gpt partitioning.
Most Windows 7 systems were BIOS with MBR(msdos) partitioning, but a few were UEFI. And recent computers with i-series Intel processor may be UEFI. But many newer systems have UEFI working in CSM mode and Windows 7 installed to boot in BIOS mode.

Once a system is installed in one boot mode or the other it is very difficult to convert. Or you just erase entire drive and totally reinstall. If you have a Windows license for BIOS from your PC vendor it will not install in UEFI mode and vice-versa. You would have to purchase a full install of Windows.

New Ubuntu live installer works for both BIOS & UEFI and how you boot it is how it installs. So even if you have a newer system with UEFI, but have Windows in BIOS, you need to boot and install Ubuntu in BIOS mode.
Same if Windows is UEFI, you need to boot Ubuntu in UEFI mode to install as it will boot and install in BIOS mode to a gpt partitioned (UEFI ) drive. But then you can only dual boot from UEFI/BIOS menu not from grub.

---

### Post by jdeca57 on 2013-12-10
And another question is why would you want to use UEFI? Even Windows 8 works perfectly without it. (I upgraded a W7 PC at work) And the added security when using Ubuntu seems marginal...

---

### Post by ajgreeny on 2013-12-10
> **jdeca57 said:**
> And another question is why would you want to use UEFI? Even Windows 8 works perfectly without it. (I upgraded a W7 PC at work) And the added security when using Ubuntu seems marginal...
Having successfully installed Xubuntu 12.04 64bit on a desktop machine with UEFI, though admittedly without Windows installed on the new machine, I am not one of those who believes that legacy BIOS/CSM is the best way to go, and if possible, I suggest to all that they embrace this new system as it has a number of advantages, in particular the huge number of primary partitions available on a disk; in fact primary partitions are the only available type on a UEFI system as far as I'm aware.  I can't comment on the reported speed increase of UEFI over BIOS as I have not run this machine using BIOS mode

Read all about UEFI at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and use it if you can; it is, after all, the way everything is going from now, so you should get used to it if you can.

---

