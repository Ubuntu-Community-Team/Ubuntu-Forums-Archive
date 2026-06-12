---
title: "installing Ubuntu using grub with secure boot on."
date: 2015-10-01
forum: General Help
---

### Post by Keiichi_Akitsuki on 2015-10-01
Okay. I have been dual booting Ubuntu and Windows 8.1 but for i am giving away my machine to a non computer user who just wants Windows.
I will show step by step of what i did.

First, I deleted the partitions for Ubuntu from what i read online. then there were some that couldnt be deleted so i panicked.
Then, I just extended my windows partition.
Now is where the i became an idiot. I thought I could just restore my windows to factory settings and proceeded in doing so.
Now I am stuck in Grub.
I then proceeded in trying to install back Ubuntu using Grub.
But I couldn't "insmod loopback" because of secure boot.
Then I remembered that after I installed ubuntu, i turned back my secure boot on. I'm not sure why.
What can I do to restore back my Windows 8?

Hope help can come soon, Thank you.

---

### Post by oldfred on 2015-10-01
If it is UEFI, you should be able to go into UEFI boot tab and just choose Windows. Or one time boot key, often f10 or f12.

In the ESP - efi system partition you probably want to delete the ubuntu folder. But do not modify the Microsoft folder.
And in UEFI you can remove the ubuntu entries with efibootmgr.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo apt-get install efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr Examples:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
Really UEFI boot menu edits
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

### Post by Keiichi_Akitsuki on 2015-10-02
> **oldfred said:**
> If it is UEFI, you should be able to go into UEFI boot tab and just choose Windows. Or one time boot key, often f10 or f12.

In the ESP - efi system partition you probably want to delete the ubuntu folder. But do not modify the Microsoft folder.
And in UEFI you can remove the ubuntu entries with efibootmgr.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo apt-get install efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr Examples:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
Really UEFI boot menu edits
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

I am using ASUS and it has this fast boot thing that skips the bios and straight away goes to Grub. So I cant press f10 or f12.
Is there any other way?

---

### Post by oldfred on 2015-10-02
Cold boot to get into UEFI or BIOS
[http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006](http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006)

---

### Post by Keiichi_Akitsuki on 2015-10-06
[http://ccm.net/faq/26463-asus-laptops-accessing-the-recovery-partition](http://ccm.net/faq/26463-asus-laptops-accessing-the-recovery-partition)

I could open my thumb drive by using this and successfully installed Windows. Thank you.

---

