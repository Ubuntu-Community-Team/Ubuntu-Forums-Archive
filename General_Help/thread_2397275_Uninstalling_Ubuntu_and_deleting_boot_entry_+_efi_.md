---
title: "Uninstalling Ubuntu and deleting boot entry + efi files"
date: 2018-07-27
forum: General Help
---

### Post by rorocools on 2018-07-27
Hi, I ran into some problems in my dual boot of Ubuntu with Windows 10, and am trying to figure out how to uninstall it. I know that I have to delete the partitions Ubuntu is installed on, but am unsure of what to do after that. Some suggest I use the "efibootmgr" in a live boot of Ubuntu to reorder my boot options and delete the Ubuntu entry. I have also read that I can do this in Windows by assigning a letter to the "system" partition and going into the EFI folder and deleting the ubuntu folder. Will both of these methods (efibootmgr vs. windows method) accomplish the same task? 

Also, is it safe to delete the linux swap partition if I am uninstalling Ubuntu?

Thanks for your help.

---

### Post by oldfred on 2018-07-27
Make sure you change boot order to directly boot Windows from UEFI as first. Otherwise you may get grub> boot error as once Ubuntu is deleted but you still have Ubuntu as first, it may try to boot it, but it has no boot files, just UEFI boot entry.

The efibootmgr is to delete the boot entry in UEFI. You may be able to do that directly in UEFI. 
Not sure if Windows has anyway to directly do that.

You also have /EFI/ubuntu folder in your ESP - efi system partition. Windows does not normally mount ESP, but you can mount it,  and then delete /EFI/ubuntu folder. Do not delete /EFI/Microsoft folder or all of ESP as that is your Windows boot files.

You can just delete any partitions Ubuntu created. Windows does not correctly show Linux partition, so sometimes dangerous unless you know for sure which is which. You have other Windows partitions like the ESP, reserved,  or recovery that it does not normally show and you do not want to delete those.

[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720)
       Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

### Post by rorocools on 2018-07-27
Ok, how can I mount the ESP?

---

### Post by oldfred on 2018-07-27
If using the Ubuntu live installer, you can use gparted, Disks, just click on it with Naulitus file manager.
Not sure how in Windows? I think I have seen in some Windows forums how to do that. 

If using terminal in Ubuntu live. ESP may be sda2 or even sda3. First check partitions.
sudo parted -l
       mkdir /mnt/efi
mount /dev/sda1 /mnt/efi

---

### Post by rorocools on 2018-07-27
Alright, so my understanding is that mounting the partition is basically the same as assigning it a letter to be accessed through a command-line. If I use efibootmgr to delete the entry through a live ubuntu session, can I reboot back into windows to mount the partition and delete the ubuntu EFI data? Or, will the entry that I deleted already have been recreated? I only say this because I am familiar with the drive letter assignment in Windows but not Ubuntu. Again, thank you for all your help.

---

### Post by oldfred on 2018-07-27
There are three parts.

The UEFI entry. That must be reset to Windows as default before deleting Ubuntu partitions or ESP folder.
The ESP folder at /EFI/ubuntu has part of grub boot files.
The Ubuntu partition(s) which are / (root) at minimum. Then swap or other partitions are optional.

---

