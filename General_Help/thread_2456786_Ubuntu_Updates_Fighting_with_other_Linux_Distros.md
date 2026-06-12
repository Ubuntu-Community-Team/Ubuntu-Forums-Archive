---
title: "Ubuntu Updates Fighting with other Linux Distros"
date: 2021-01-19
forum: General Help
---

### Post by kotoff on 2021-01-19
Many of the Ubuntu updates include an update to grub. This update is changing my boot order and I am looking for a easy way to prevent it from happening. I have a triple boot system Manjaro in 1, Ubuntu in 2 and Fedora in 3. I am using GPT (Black Screen Grub) not MBR (Purple Screen Grub). I just did the last update and it switched my grub boot to MBR on partition 2. I am fixing it by using efibootmgr -o but I would like to disable any update from changing my grub settings. Is this possible and if so how? A link to instructions would be appreciated.

---

### Post by yancek on 2021-01-19
If you are using EFI, you should have boot options in the BIOS firmware that can set which OS is used for the primary bootloader.  If you don't change that, doing an update including Grub and the kernel should have no effect.  With EFI, there is no boot code in the MBR.  If you can't resolve this, I would suggest you go to the site below and download boot repair according to the instructions there and only select the option to Create BootInfo Summary.  When it finishes, you should get a link which you can post here for help.

   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

