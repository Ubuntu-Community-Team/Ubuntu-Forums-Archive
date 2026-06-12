---
title: "Windows won't show up in bootloader"
date: 2018-06-30
forum: General Help
---

### Post by camtlmao on 2018-06-30
Hi, I'm incredibly new to Linux and I've never used these forums either, so my apologies if this is the wrong place to ask. So my problem is that I have Windows 10 Pro installed on one NTFS partition and then I have Ubuntu 18.04 LTS installed on an Ext3 partition, so, normal stuff. But when I boot into grub it only gives me the option to boot into Ubuntu, not windows. So the largest (157 GB) one is the windows partition, and the 98 GB Ext3 is the partition where Ubuntu is installed, I'm not entirely sure if this is helpful or not, but I don't really know what I'm doing :/
 [ATTACH=CONFIG]280257[/ATTACH]
Quick edit, my apologies, it appears that the bootloader doesn't even show up anymore, it boots straight into Ubuntu.

---

### Post by yancek on 2018-06-30
Can't really tell from the output you posted but it appears you have a BIOS boot partition (1MB) and maybe an EFI partition.  Boot Ubuntu and run the command below and post the output here (that is a Lower Case Letter L in the command.

```
sudo parted -l
```

While you are waiting for a response, you might go to the link below and use the 2nd option to download boot repair.  Once downloaded, run it per the instructions on the page and use the Create BootInfo Scxript option.  Do NOT try to make any repairs.  Post a link to the outpt here for help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by camtlmao on 2018-06-30
1. So here is what showed up after I used the command.
[ATTACH=CONFIG]280261[/ATTACH]
2. While I was waiting for a response (earlier) I found another forum for boot repair, but it told me that it wouldn't work in legacy mode, so I put it on a USB pendrive and booted into it, however, it would only let me boot from legacy, not UEFI, so I have no idea what to do at this point. If I followed any of these instructions wrong, please tell me

---

### Post by Hund on 2018-06-30
Any particular reason you're using Ext3 and not Ext4?

Regarding GRUB, make sure you have the package `os-prober` installed and then run the command below to update your GRUB configuration. It should hopefully find your missing Windows partition as well.


```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by yancek on 2018-07-01
You have an incompatible install as you had windows using UEFI/GPT and you installed Ubuntu Legacy/GPT.  You can either re-install Ubuntu UEFI or go to the Ubuntu documentation site below and read it thoroughly paying particular attention to the section about converting Ubuntu to UEFI.  A Legacy install of a Linux system won't boot/chainload a windows UEFI install.  If you have an option in the BIOS to boot from EFI file, you can probably find the windows boot entry there and boot it.  If that worked and you then wanted to boot Ubuntu, you would have to go through the same process using the BIOS and change to legacy.  IPartition 7 in your Parted output is the BIOS-grub partition while partition 4 is the EFI partiiton.  If you want to boot both with options in the Grub menu, you need to convert Ubuntu to UEFI or re-install Ubuntu UEFI.  Read the documentation below and decide which option you want.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

