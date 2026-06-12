---
title: "Putting second HD into new Win10 machine"
date: 2016-11-15
forum: General Help
---

### Post by Autodave on 2016-11-15
I am thinking about buying a new computer. It would have Win 10 already installed. One HD in it. I would like to put a second HD (SSD) in it and have Xubuntu running on that HD. The SSD would already have Xubuntu installed on it. How do I go about getting this to work?

Thanks in advance for your help.

---

### Post by oldfred on 2016-11-15
If new computer then it will be UEFI.
Grub only installs its boot loader to the ESP - efi system partition on the drive seen as sda.
So which drive will be sda? That will depend on the SATA port order. First SATA port or SATA0 will normally be sda.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If external drive bit more complicated.

Is current drive have Xubuntu configured for UEFI boot, or old install with BIOS/MBR?

---

### Post by Autodave on 2016-11-15
I would like the SSD (what I am using right now) to be the main drive. I believe that I disabled the UEFI a couple years ago to get Xubuntu on the drive then.

---

### Post by irongolem0982 on 2016-11-15
Going off what @[COLOR=#000000]oldfred said[/COLOR] I would say just try it!

Plug the SSD with Xubuntu on it into the lowest number SATA slot, and the Windows 10 drive into the second lowest number SATA slot. (SATA 0 being the lowest number on some machines, other machines SATA 1) then configure the bios or uefi to boot from the Xubuntu drive/ssd. 

If it boots fine then just run ```
sudo update-grub
``` then grub will recognize the windows 10 drive and present you with a boot selection menu upon reboot

If it does not boot then you will need to reinstall Xubuntu under the uefi such that it will work. 

Good Luck!!!

---

