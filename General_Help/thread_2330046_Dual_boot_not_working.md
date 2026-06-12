---
title: "Dual boot not working"
date: 2016-07-07
forum: General Help
---

### Post by avents on 2016-07-07
My laptop has Ubuntu 14.04 LTS  and Windows 10.
But Win does not boot.

$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
done

I don't know about EFI  and don't understand how it got uploaded 
Thanks

---

### Post by avents on 2016-07-07
Boot info summary: 

   [http://paste.ubuntu.com/18703497/](http://paste.ubuntu.com/18703497/)

---

### Post by grahammechanical on 2016-07-07
Did you recently re-install Ubuntu 14.04?

---

### Post by oldfred on 2016-07-07
You have a gpt partitioned drive. So Windows only boots in UEFI boot mode.
And you have (had?) Ubuntu installed in UEFI boot mode as it shows /EFI/ubuntu in ESP - efi system partition.

But now you also show a BIOS boot version of grub in MBR that is not installed correctly, but should never be used anyway.
Best just to never boot in BIOS mode as neither Ubuntu nor Windows will work in that mode.

If you have Secure boot on, it may be better to have it off.
From grub menu you cannot boot Windows with Secure boot on. You can boot Windows directly from UEFI boot menu or one time boot key with Secure boot on.

---

### Post by avents on 2016-07-09
> **oldfred said:**
> ....

If you have Secure boot on, it may be better to have it off.
From grub menu you cannot boot Windows with Secure boot on. You can boot Windows directly from UEFI boot menu or one time boot key with Secure boot on.

I did not find "**Secure boot**"  in BIOS.
But I saw that** Legacy **was enabled  so I disabled it - yet it made no difference.
And I asked boot-repair to **repair grub**.
Here is what it says:

"Boot successfully repaired.
Please write on a paper the following URL:
[http://paste.ubuntu.com/18719018/](http://paste.ubuntu.com/18719018/)
In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.
You can now reboot your computer.

The boot files of [The OS now in use - Ubuntu 14.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)).

You may want to retry after deactivating the [Backup and rename Windows EFI files] option."

Boot-repair says : "Boot successfully repaired."  But in actuality still cannot boot Windows

---

### Post by oldfred on 2016-07-09
Grub only boots working Windows.
That means no hibernation nor fast start up in Windows, nor Windows needing chkdsk.
Grub also will not boot Windows with Secure Boot on. Something about the keys & signed file chain not correct currently.

You still should be able to directly boot Windows from UEFI or UEFI one time boot key like f10 or f12.

But line 598 says this:
 SecureBoot maybe enabled.  

It may not directly be labeled secure boot. Many systems use "Windows" and "Other" and notes say if you install Windows 7 you must use "Other". 
Windows 7 is also not Secure Boot enabled.

---

