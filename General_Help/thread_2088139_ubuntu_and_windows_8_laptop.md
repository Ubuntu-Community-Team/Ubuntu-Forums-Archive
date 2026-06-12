---
title: "ubuntu and windows 8 laptop"
date: 2012-11-25
forum: General Help
---

### Post by terry_gardener on 2012-11-25
I have recently purchased and new samsung 3 series laptop and have a couple of questions. 

1. since it doesn't boot when secure boot enabled when you disable it you get 3 options uefi os, csm os and uefi and legacy os which is the best to choose?

2. if keep the recovery partitions but removed windows 8 and installed ubuntu will the recovery to factory settings still work via the f4 at boot up stage just incase it needs to go back for any reason. 

3. it comes with the amd a8-4500 cpu and amd radeon hd 7640G grpahics how is the amd drivers in ubuntu and as i have only ever used nvidia in the past with ubuntu 

4. is there anything that i have to watch out for when installing ubuntu 12.10 on uefi hardware.

---

### Post by Mark Phelps on 2012-11-25
From what I've read recently, there still is no workaround to the Secure Boot problem, so anything you do is going to carry some risk.

Once you reformat your PC, the Win8 reset option will NOT work.  IF you want a way to RESTORE your laptop to its current state later, the best solution at present is to image it off to an external drive -- but you need to be sure to do that with a Window solution that understands UEFI Booting.

The Linux community is always playing catch-up with new hardware because in nearly all cases, the hardware vendors aren't bothered to write Linux drivers.  I've seen your situation referred to as "hybrid Crossover" and, as far as I know, NO, there are no Linux drivers available yet to handle that.

As to UEFI hardware, YES there are things to watch out for -- but since I don't have that, can't provide you specifics.

---

### Post by dsr3 on 2012-11-25
I allowed Ubuntu to be installed along side of Windows 8 on a Lenovo s405. It works as long as you allow Legacy in the boot options of the BIOS. This way I've kept the Windows 8 install as well as it's restore partition.

I'm having some screen brightness issues, but that's the only problem.

---

### Post by oldfred on 2012-11-26
You can install to many computers with secure boot. But each vendor has implemented UEFI differently and some work better than others.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

[http://www.linlap.com/samsung](http://www.linlap.com/samsung)
Only comment I could see was turn off quick boot.

But if you use Windows to shrink the Windows NTFS partition you can create your Linux partitions without any issues as gpt partitioning does not have the old MBR 4 primary partition limit.

Ubuntu 64 bit 12.10  has implemented secure boot with grub2 2.00 and users have posted it works. Some have said after install it works with either secure boot on or off.

Boot-Repair has been updated to fix BIOS type installs in UEFI computers and add a correct chain load entry to Windows as grub2 os-prober only creates a BIOS type entry not a efi entry.

       Secure Boot:
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY)
[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

       Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

   UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
Acer V5-571P-6815
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

Not sure about AMD video, some discussions seem to say it is still not as well supported as nVidia.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIzNDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTIzNDQ)

---

### Post by Parker32 on 2012-11-26
Ubuntu is best for any laptop

---

### Post by terry_gardener on 2012-11-29
thank you all the advice.

---

### Post by YannBuntu on 2012-11-29
Hello

> **terry_gardener said:**
> 1. since it doesn't boot when secure boot enabled

Do you mean you can't boot on an Ubuntu disk when SecureBoot is enabled?
Have you tried to boot a Ubuntu **12.10 64bit** liveCD (or liveUSB) ?

> **terry_gardener said:**
> when you disable it you get 3 options uefi os, csm os and uefi and legacy os which is the best to choose?

Those are options in your UEFI firmware (~BIOS), i suppose? please could you show us a picture?

> **terry_gardener said:**
> 2. if keep the recovery partitions but removed windows 8 and installed ubuntu will the recovery to factory settings still work via the f4 at boot up stage just incase it needs to go back for any reason.

Not sure. I recommend you burn a Windows Recovery disk (the procedure should be indicated in your pc manual, else see [this]("http://windows.microsoft.com/is-IS/windows7/Create-a-system-repair-disc"))
Also, you don't need to remove Windows. Reducing its partition should be enough for being able to install Ubuntu.

> **terry_gardener said:**
> 3. it comes with the amd a8-4500 cpu and amd radeon hd 7640G grpahics how is the amd drivers in ubuntu and as i have only ever used nvidia in the past with ubuntu 

If you can boot on a Ubuntu live session, then the driver is ok for your pc.

> **terry_gardener said:**
> 4. is there anything that i have to watch out for when installing ubuntu 12.10 on uefi hardware.

Yes. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

