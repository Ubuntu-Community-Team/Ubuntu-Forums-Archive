---
title: "Creation of partition in laptop"
date: 2019-09-30
forum: General Help
---

### Post by AnupamMitra on 2019-09-30
I purchased a Laptop in which Windows 10 is preinstalled. Now I would like to create a partition in HDD (size 1 TB) and want to install Ubuntu 18.04 in the new partition so that both the OS would be available in the Laptop. So far my knowledge runs, alternatively, Ubuntu 18.04 can be installed as guest in Virtual Box. Which would be better in all respects?

---

### Post by yancek on 2019-09-30
If you have limited knowledge about Linux, it would probably be a lot safer to use Virtualbox and run Ubuntu that way until you are familiar with it.  Ubuntu has a site (link below) explaining dual booting it with windows 10 should you choose to do that.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dragonfly41 on 2019-09-30
The other argument for running Ubuntu in VirtualBox is that Windows 10 in doing an upgrade will not screw up Ubuntu Linux partitions which are alien to Windows. That is why I have not used my dual boot Windows 10 for months, in fear of this disruption.
But note that in Windows 10 you can install Windows Subsystem Linux (WSL) which is Ubuntu running in native Windows 10. Search "WSL setup". If you do decide to use Ubuntu I would install in a separate bootable internal drive (if you have a spare slot in laptop for another drive) or in an external USB drive (although that is not a mobile solution).

---

### Post by cruzer001 on 2019-09-30
How much ram do you have and what cpu are you running?

---

### Post by AnupamMitra on 2019-10-01
> **cruzer001 said:**
> How much ram do you have and what cpu are you running?

Thanks for reply. Installed RAM is 4 GB. Processor is Intel(R) Core (TM) i3-7020U CPU @ 2.30 GHz.

---

### Post by AnupamMitra on 2019-10-06
I followed the guidelines provided in the following link and issue stand resolved.

[https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)

---

