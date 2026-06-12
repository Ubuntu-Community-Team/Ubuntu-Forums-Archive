---
title: "grub boot problem after deleting partition"
date: 2023-01-25
forum: General Help
---

### Post by skpacman8629 on 2023-01-25
I had 18.04 and 20.04 installed on my laptop in separate partitions and grub would bring up a menu of the two options to boot from, but I no longer needed 20.04, so I deleted its partition and expanded the 18.04 partition to take up the free space.

Now when I boot, it just goes to the `grub>`prompt without booting into 18.04

How do I fix this in grub without losing my current partition full of stuff for my job?

---

### Post by tea for one on 2023-01-25
> **skpacman8629 said:**
>  but I no longer needed 20.04, so I deleted its partition and expanded the 18.04 partition
I would bet that 20.04 was controlling Grub.
> Now when I boot, it just goes to the `grub>`prompt without booting into 18.04
Ubuntu 18.04 reaches End of Life in April 2023
> How do I fix this in grub without losing my current partition full of stuff for my job?
Do you have a recent (i.e. yesterday) data backup?
If not, this is your first and most important task.

Then, I would suggest that you do not waste any more time trying to fix Grub.
Download and install Ubuntu 22.04 (or your favourite flavour) and restore your data backup.
Remember to install in UEFI mode with GPT.

---

### Post by yancek on 2023-01-25
The scenario you describe would indicate the default bootloader (Grub) was from the installation of 20.04.  You will need to reinstall Grub pointing to the 18.04 installation and the best way to do that would be using the USB you used to install 18.04.  THe link below describes several methods of doing it and is the Ubuntu documentation site so read through it, particularly Section 2.  Also, you are aware that support for 18.04 will end in April of this year are you not?

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

If you are using an EFI system it is a bit different and the link below gives an explanation.  If you have trouble understanding it, just do an online search for reinstalling Grub2 EFI on Ubuntu and you should get a number of sites.

[https://techbit.ca/2018/09/repair-grub2-efi-boot/](https://techbit.ca/2018/09/repair-grub2-efi-boot/)

---

