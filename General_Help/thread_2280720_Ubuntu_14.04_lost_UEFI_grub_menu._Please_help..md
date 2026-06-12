---
title: "Ubuntu 14.04 lost UEFI grub menu. Please help."
date: 2015-06-01
forum: General Help
---

### Post by kagashe on 2015-06-01
I am having Ubuntu 14.04 with LTS Hardware Enabled i.e. Ubuntu 14.04.2 installed on Lenovo G50-45 with Windows 8.1 in dual boot.

Yesterday I installed Ubuntu 15.04 on 32 GB USB stick using this machine and selected grub install on the USB stick thinking that the grub on hard disk will remain intact.

I could successfully use the Ubuntu 15.04 installation on the USB stick.

Now I discovered that I have lost the grub menu on the hard disk and I have to use the USB stick to boot into Ubuntu 14.04.2 on hard disk.

If I plug out the USB stick I am getting grub command line which I am not familiar with.

Please tell me step by step how to restore the grub menu on hard disk.

Kamalakar

---

### Post by papibe on 2015-06-02
Hi  kagashe.

You can solve your problem using a LIVE CD/USB.

First, remove the 15.04 USB stick.

Boot into the installation media, and select 'Try Ubuntu'. When you get to the desktop follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") to reinstall/reconfigure grub.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by kagashe on 2015-06-02
> **papibe said:**
> Hi  kagashe.

You can solve your problem using a LIVE CD/USB.

First, remove the 15.04 USB stick.

Boot into the installation media, and select 'Try Ubuntu'. When you get to the desktop follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") to reinstall/reconfigure grub.

Hope it helps. Let us know how it goes.
Regards.I have read about this but I am scared to use it because most documents are telling me that /boot/efi partition is generally /dev/sda1 but in my case it is /dev/sda2. The /dev/sda1 is an NTFS partition used by Windows.

Kamalakar

---

### Post by kagashe on 2015-06-02
> **papibe said:**
> Hi  kagashe.

You can solve your problem using a LIVE CD/USB.

First, remove the 15.04 USB stick.

Boot into the installation media, and select 'Try Ubuntu'. When you get to the desktop follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") to reinstall/reconfigure grub.

Hope it helps. Let us know how it goes.
Regards.
I used Ubuntu 15.04 Live USB stick, installed Boot-Repair through PPA(ppa:danielrichter2007/grub-customizer)
Before going for Recommended Repair I clicked for Advanced Options and confirmed that it was showing /boot/efi on sda2 which is there in my case.

The Grub Menu is restored and I can boot into Ubuntu 14.04.2 but there are many entries which are not needed.
Note: I installed Grub Customizer through PPA and removed the unwanted Custom entries in the menu.

Thanks for the support.

Kamalakar

---

### Post by oldfred on 2015-06-02
If exactly same version of grub, you only needed to edit the grub.cfg in your ESP - efi system partition.

The grub.cfg in the efi has a configfile entry to find the grub.cfg in the install it will boot.

Typical entry, you would have to change UUID & drive, partition to correct install.

 search.fs_uuid [COLOR=#ff0000]Your-uuid-here[/COLOR] root hd[COLOR=#ff0000]0[/COLOR],gpt[COLOR=#ff0000]8[/COLOR]
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

If you know drive, partition, you can make it one line. But if drive order may change like a flash drive better to use above version.


 configfile (hd[COLOR=#ff0000]0[/COLOR],gpt[COLOR=#ff0000]7[/COLOR])/boot/grub/grub.cfg

---

