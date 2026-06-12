---
title: "Booting from USB- an issue"
date: 2016-11-02
forum: General Help
---

### Post by isolated-thinker on 2016-11-02
Greetings!

I am running 16.04 LTS on my Dell laptop.

I  have a few different Live distros that I boot to from USB now and then  for various reasons. In my BIOS, I have the boot order set to boot from  USB first, then, CD, then the hard drive boot partition. 

However,  ever since I installed Ubuntu on my laptop, the boot order is ignored. I  need to go to the BIOS settings, and save and exit before the defined  boot order is acknowledged.

I (along with Google) am at a loss as to how to fix this small, yet highly annoying issue.

---

### Post by oldfred on 2016-11-02
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I find if multiple ISO better to have all on one flash drive or even on hard drive and then use grub to loopmount directly boot them.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by isolated-thinker on 2016-11-08
Thank you for the info! (sorry for the late reply).

Hopefully I will give the links a go tonight.

---

