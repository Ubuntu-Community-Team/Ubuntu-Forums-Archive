---
title: "Dual booting issue"
date: 2016-12-16
forum: General Help
---

### Post by mtmasterg on 2016-12-16
I just installed Kubuntu, with windows already installed. Now, when I boot, it ONLY boots to kubuntu. It does not give me an option to boot to windows instead. How can I choose which OS to boot to?

---

### Post by oldfred on 2016-12-16
Did you try?
sudo update-grub

If that does not work:
       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by cdtech on 2016-12-16
I can leave you with a link, a tutorial on the Grub2 boot loader.It's a very detailed tutorial.

> Learn how to work with GRUB 2, add and remove menu entries, customize titles and boot options, dual-boot and triple-boot operating systems

---

### Post by mtmasterg on 2016-12-17
> **oldfred said:**
> Did you try?
sudo update-grub

If that does not work:
       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Here is the link from it :)
[http://paste2.org/UB40XGA6](http://paste2.org/UB40XGA6)


> **cdtech said:**
> I can leave you with a link, a tutorial on the Grub2 boot loader.It's a very detailed tutorial.
Sure! I would love to see that.

---

### Post by oldfred on 2016-12-17
You have Windows installed on gpt partitioned drive in UEFI boot mode. You should be able to directly boot it from UEFI's boot menu often f10 or f12. But may have to turn on UEFI boot or turn off CSM/BIOS/Legacy boot in UEFI.

You have Ubuntu installed in BIOS boot mode, but no bios_grub partition. I am surprised grub installed correctly. With BIOS boot on gpt partitioned drive it needs a 1 or 2MB unformatted bios_grub partition. If you want to keep BIOS boot use gparted to add a small partition and add bios_grub flag.

Better to configure Ubuntu for UEFI boot. But you would also have to boot live installer in UEFI mode, as Boot-Repair says you booted flash drive in BIOS mode. If you boot in UEFI mode and run in advanced options the full uninstall/reinstall of grub it will uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

How you boot install media is then how it installs. And if Windows is UEFI best to have Ubuntu in UEFI boot mode. 
UEFI and BIOS are not compatible, they write data for system onto drive differently. So once you start booting in one mode from UEFI boot menu, you cannot switch to another system in the other boot mode. Or from grub you can only boot systems installed in same boot mode.

Some do just dual boot from UEFI boot menu.

---

