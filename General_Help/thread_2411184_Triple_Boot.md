---
title: "Triple Boot"
date: 2019-01-26
forum: General Help
---

### Post by joe7 on 2019-01-26
I guess this is really a GRUB question but maybe someone can help?

I have created multi boot machines many times in the past and I am sure that I have managed to do this before.

Can anyone explain how I would have 2x Windows 10 installations and Ubuntu sowing in GRUB; at the moment I have Ubuntu and then the option for windows is for the Windows boot option screen as opposed to having the 3 OSs in GRUB.

---

### Post by oldfred on 2019-01-26
Are all installs UEFI or all BIOS base boot?

Windows only boots from one primary NTFS partition with boot flag in BIOS mode. And second install of Windows overwrites the boot files in boot partition, and adds other Windows to BCD. So grub only finds boot files in one partition.

Windows also only boots from the ESP - efi system partition at /EFI/Microsoft with UEFI boot. So only one boot entry.

There are work arounds where you can create ways for grub to boot second installs, but different if UEFI or BIOS.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by joe7 on 2019-01-28
Thank you.

heres the link 

[http://paste.ubuntu.com/p/k9VBqjYfSX/](http://paste.ubuntu.com/p/k9VBqjYfSX/)


Thanks Again

---

### Post by joe7 on 2019-01-28
Thank you.

heres the link 

[http://paste.ubuntu.com/p/k9VBqjYfSX/](http://paste.ubuntu.com/p/k9VBqjYfSX/)


Thanks Again

---

### Post by yancek on 2019-01-28
Which systems (Ubuntu or either windows) boot?  Your boot repair output shows that you have windows code in the MBR of the first 4 hard drives and Grub code in the MBR of the 5th (sde) drive with the core.img file present looking for the rest of the necessary Grub files on sde5.  Boot repair usually shows these files but they are not shown in your output.  However, these files show on sdd3.  Did you do 2 (or more) installs of Ubuntu?  Your situation is as mentioned in the second sentence of the post above by oldfred so you will need to use some workaround to have both windows entries on your grub menu.  I don't know any so can't help with that.

I notice the only Legacy/MBR drive you have is sdd, the 1.8TB drive and the other 4 are GPT and my understanding is that to have a functioning windows OS on a GPT, you need to use UEFI with an EFI partition on at least one drive.  You don't have that.  The only partition which shows windows boot files is sdd2 but that may be because they were not detected by boot repair.  You do have 1 or more windows partitions on each drive but it isn't clear what the status is?  Is your question theoretical or do you actually have 2 windows 10 installs along with Ubuntu and if so, which boot?

---

### Post by oldfred on 2019-01-28
Boot-Repair's report uses bootinfoscript as first part of report. And bootinfoscript has not yet been updated to show NVMe & MMC drives, so only later parts of report show that you have NVMe drive. 
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

Windows only boots in UEFI mode from gpt drives and only in BIOS mode from MBR drives.
So since you have an ESP (vfat or fat32) in the NVMe drive, that must be the way you are booting as Windows boot loader in MBR of gpt will never work. 
Windows installs to a drive may install boot files into another drive if that other drive is set as default in UEFI/BIOS.
No reason to have Windows BIOS boot loaders in MBR of gpt drives, it will never work. 

You cannot mix UEFI & BIOS boot (easily). It is only possible to manually boot from UEFI boot menu installs in different boot modes.
Windows will not boot from external drives, so if external drive is a Windows install it will not boot. You show it as MBR, but I would consider converting to gpt, so all drives are gpt. If you want it bootable and gpt, it must have an ESP and/or a bios_grub depending on boot mode you want to use. If you just repartion it, it will erase it, but there are conversion tools that should work  without erasing data (but backups still required).

See line 728 of report, you directly get same info with this:
sudo efibootmgr -v
See also 
man efibootmgr

You have many UEFI boot entries and a lot look like duplicates. Some UEFI if too full will create major issues. There was an old bug where if UEFI memory was half full system would lock up. So essential to houseclean out duplicate entries.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

