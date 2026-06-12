---
title: "Broken Grub uefi"
date: 2023-03-08
forum: General Help
---

### Post by unknown122 on 2023-03-08
I installed my grub in my chrooted environment by issuing grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=UBUNTU and run grub-mkconfig -o /boot/grub/grub.cfg and also grub-mkconfig -o /boot/efi/EFI/UBUNTU/grub
cfg after rebooting into the grub I get the following errors: 
error: no device found <uuud> <- it's looking for my root to which the uuid it's looking for doesn't come close my root uuid 
error: no server found <- I literally have no idea what that means 
error: please load kernel first 

grub-rescue> <- this is the grub-rescue shell. If you're here, you must of screwed up somewhere which is where I am at


I also have tried using dpkg-reconfigure grub-efi-amd64 and adding dm_encrypt lvm2 into my modules for initramf-tools 
My installation consists of uefi + luks + lvm and please do keep in mind my fat32 partition which has the boot,esp flag enabled is not encrypted but my whole system is. 
For example, I expect my kernel to prompt me a password to unlock my luks device to which the initrd will setup my system and boot the machine. My /etc/crypttab already has my uuid to which I know very well it is the right one. 
I also edited the cryptsetup-initramfs/conf-hook where I uncommented ASK PASS=y 

And yet, I still get the same exact errors I mentioned before. This installation has worked before in the past where my fat32 partition was mounted on /boot which it should not be because if it's on that point, dpkg cannot create symlinks and will cause the package to fail. 
I do not want my esp partition on /boot I want it on /boot/efi

Please help me

---

