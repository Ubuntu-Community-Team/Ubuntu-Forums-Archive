---
title: "Restoring Grub After Arch Install"
date: 2006-07-13
forum: General Help
---

### Post by Phlosten on 2006-07-13
I thought I would have a look at Arch Linux the other day and proceeded to install it upon my second partition. I let it install it's grub and now my pc boots and grub reads the /boot/grub/menu.lst from the Arch partition.

I edited that file to add the boot info for my main partition (Ubuntu) so I could boot back into Ubuntu. Now I have finished playing around with Arch (Ubuntu still the best for me) I wanted to restore grub back to the way it was, ie reading from the Ubuntu partition. I want to clear the Arch partition for storage purposes.

I thought it was as simple as booting into Ubuntu then doing a 'grub-install /dev/hda' but I get the following error.

/dev/hda does not have any corresponding BIOS drive.

Can someone point me to the way to restore my grub. The only other way I can think of is doing a reinstall of Ubuntu, but I really don't want to do that.

---

### Post by chameleonkid on 2006-07-13
How do you want to remove arch? To clear the menu entry of GRUB you must sudo edit the /boot/grub/menu.lst file. To remove arch from your system, use gparted or similiar.

Edit: I am using arch right now, and I found it kind of a hassle to setup but surprisingly fast.

Edit2: If you installed Arch's GRUB bootloader, and you want to get Ubuntu's grub bootloader to work again, install the GRUB loader in ubuntu, either through synaptic or aptitude or from the rescue disk on the alternate install cd.

---

