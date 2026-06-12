---
title: "Cannot load Windows 7 after first time installation of Ubuntu."
date: 2020-02-29
forum: General Help
---

### Post by thundrstrike on 2020-02-29
I am very new to linux. I installed Ubuntu(18.04.4 LTS) alongside my  Windows 7(x64). Even though I can boot into Ubuntu without any problems  whenever I select Windows 7 from the grub menu the screen is just frozen  with a wine color on it. Grub says that my Windows is on sda1 while I  have checked that the windows files are on sda3. I have attached the  scrshot of fdisk -l command on ubuntu. Any help is appreciated. Thanks          
[ATTACH=CONFIG]285111[/ATTACH]

---

### Post by CelticWarrior on 2020-02-29
Was Windows booting fine before you installed? No errors in the partitions? Nothing weird happening?

Grub can only boot working Windows.

---

### Post by yancek on 2020-02-29
You installed Ubuntu incorrectly as an EFI install while your windows is  a Legacy install.  The Ubuntu Grub bootloader installed in EFI mode (sda6 shows as EFI partition)   will not boot a Legacy windows system.  The fdisk output shows the disk type as dos which means windows is Legacy.  Make sure you boot Ubuntu Legacy and do not install EFI.  THis is explained at the Ubuntu documentation site at the link below.  Read the General Principles and then scroll down to the section where it explains identifying if computer boots in EFI mode, don't do that.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by CelticWarrior on 2020-02-29
> **yancek said:**
> You installed Ubuntu incorrectly as an EFI install while your windows is  a Legacy install.  The Ubuntu Grub bootloader installed in EFI mode (sda6 shows as EFI partition)   will not boot a Legacy windows system.  The fdisk output shows the disk type as dos which means windows is Legacy.  Make sure you boot Ubuntu Legacy and do not install EFI.  THis is explained at the Ubuntu documentation site at the link below.  Read the General Principles and then scroll down to the section where it explains identifying if computer boots in EFI mode, don't do that.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Good catch. I could barely read the screenshot in the small screen I'm now.

Yes, this is the reason.

---

### Post by CelticWarrior on 2020-02-29
Maybe it can be converted to Legacy by simply installing grub-pc, the MBR already saves a step.

```
sudo apt install grub-pc
```
```
sudo grub-install /dev/sda
```

I'm not sure about uninstalling Grub for UEFI...

Then in UEFI ("BIOS") settings change to "Legacy/CSM only" to force Legacy mode.
If it boots to the Grub menu you're good but boot in Ubuntu first just in case. Then reboot and try Windows.


And the obligatory information: Windows 7 is EoL, out of support, shouldn't be used.

---

### Post by thundrstrike on 2020-03-01
Hey I finally got it working. I don't know how but I tried a bunch of different things including the things you guys told me to do. Thanks!

---

