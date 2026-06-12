---
title: "Error During Bootup Related To Secure Boot"
date: 2016-08-04
forum: General Help
---

### Post by sasafrass452 on 2016-08-04
This issue is related to my other thread here: [https://ubuntuforums.org/showthread.php?t=2331312](https://ubuntuforums.org/showthread.php?t=2331312)

After using the method that I linked to in the above thread, I now see something like "error loading in-kernel x.509 certificate (-74)" appearing during bootup. My research indicates that this is related to "secure boot" being enabled. However, I *thought* I disabled it while installing Ubuntu, though I'm not 100% sure. Why would I be seeing this error, if it's disabled? How can I verify if it's disabled? If not, can it be disabled? If so, how?

---

### Post by oldfred on 2016-08-04
I do not know AMD systems.

But most UEFI now do not call it UEFI Secure boot, but "Windows" or "Other". Fine print somewhere will often say if Windows 7 you must use "Other". And that is because Windows 7 does not support Secure boot.

---

### Post by sasafrass452 on 2016-08-05
Well, I installed cpu-checker which is supposed to tell me if something is enabled/disabled on the cpu. I would like to know if secure boot is enabled. But how do I run cpu-checker?

---

### Post by Dennis N on 2016-08-05
You can check and set the secure boot status in the computer's UEFI firmware. There is a good discussion (with screen shots) of Secure Boot and how to disable it here:

[http://www.rodsbooks.com/efi-bootloaders/secureboot.html#disable](http://www.rodsbooks.com/efi-bootloaders/secureboot.html#disable)

---

### Post by sasafrass452 on 2016-08-05
I tried pressing fn+f2 as instructed, but the BIOS didn't appear. Will cpu-checker work? How do I run it?

> **Dennis N said:**
> You can check and set the secure boot status in the computer's UEFI firmware. There is a good discussion (with screen shots) of Secure Boot and how to disable it here:

[http://www.rodsbooks.com/efi-bootloaders/secureboot.html#disable](http://www.rodsbooks.com/efi-bootloaders/secureboot.html#disable)

---

### Post by oldfred on 2016-08-05
UEFI/BIOS are not directly related to cpu.

Why cpu-checker, that is more for what settings are inside cpu, not UEFI/BIOS?
Supported feature tests are NX/XD and VMX/SVM.
Note sure if then it now has added anything related to UEIF or BIOS?

If you can get to grub menu with Escape if UEFI or hold shift if BIOS from Vendor logo on cold reboot.
Last entry in grub menu will take you to UEFI.

      ```
 ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup 
 } 
```

---

### Post by sasafrass452 on 2016-08-07
I tried your code, but terminal said "command not found". :confused: What exactly is it supposed to do?

> **oldfred said:**
> UEFI/BIOS are not directly related to cpu.

Why cpu-checker, that is more for what settings are inside cpu, not UEFI/BIOS?
Supported feature tests are NX/XD and VMX/SVM.
Note sure if then it now has added anything related to UEIF or BIOS?

If you can get to grub menu with Escape if UEFI or hold shift if BIOS from Vendor logo on cold reboot.
Last entry in grub menu will take you to UEFI.

      ```
 ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup 
 } 
```

---

### Post by oldfred on 2016-08-07
That is not a terminal command, but a menu entry in grub to reboot back into UEFI.

---

### Post by sasafrass452 on 2016-08-28
Can anyone help me resolve this?

---

### Post by oldfred on 2016-08-28
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What brand/model system? What video card/chip?

---

### Post by sasafrass452 on 2016-08-29
I have a laptop, a Lenovo G50.
My video chip is AMD Radeon R5 Graphics × 4, Gallium 0.4 on AMD MULLINS (DRM 2.43.0, LLVM 3.8.0).

> **oldfred said:**
> May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What brand/model system? What video card/chip?

---

### Post by oldfred on 2016-08-29
Have you seen the  issues on AMD?
You have to be sure the current open source works, or if you need the proprietary driver then 14.04 may be better if not a brand new system which might otherwise need 16.04.

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075) 
   
Note new 
AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)
How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

---

### Post by sasafrass452 on 2016-08-29
My laptop is a little over a yr old. I have 16.04 installed fresh, with updates. Somewhere along the way, the boot splash screen disappeared. I then used a script which I've linked to in my other thread about that issue, which caused the error I described in this thread. My mother has the same laptop, with 16.04 installed fresh with updates, yet the splash screen still appears during boot up. I just can't figure out what, if anything, I did to cause this issue.

> **oldfred said:**
> Have you seen the  issues on AMD?
You have to be sure the current open source works, or if you need the proprietary driver then 14.04 may be better if not a brand new system which might otherwise need 16.04.

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075) 
   
Note new 
AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)
How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

---

