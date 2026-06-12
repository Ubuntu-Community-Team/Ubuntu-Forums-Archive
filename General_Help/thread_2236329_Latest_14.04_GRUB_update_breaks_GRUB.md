---
title: "Latest 14.04 GRUB update breaks GRUB"
date: 2014-07-26
forum: General Help
---

### Post by Sieges on 2014-07-26
[FONT=verdana]Hello,

I installed the latest 14.04 updates (including grub updates) on my laptop and now the grub seems broken. I cannot boot.
I had a nightmare when updating from 13.10 to 14.04 trying to get GRUB to work (the infamous [/FONT][COLOR=#333333]grub_term_[/COLOR][COLOR=#333333]highlight_[/COLOR][COLOR=#333333]color error)[/COLOR]

[FONT=verdana][COLOR=#333333]Now i dont get any error but Ubuntu does not boot. I have tried Legacy and UEFI mode in BIOS. Seems that it is broken. Anyone else have had this and knows how to fix it?
The Boot-Repair CD?

Using a Sony Vaio Pro Haswell Laptop, only running Ubuntu. No Dual Boot.[/COLOR][/FONT]

---

### Post by thibault3 on 2014-07-26
Yes, I fixed this with boot-repair.
I used my ubuntu cd to boot and then install boot-repair from there, the live cd didn't work for me.
Here's the link to my solution, choose second option, in my opinion the best
[http://help.ubuntu.com/community/Boot-Repair](http://help.ubuntu.com/community/Boot-Repair)
Good Luck!

---

### Post by Sieges on 2014-07-26
Thanks for the reply.
I will give it a bash this evening!

---

### Post by Sieges on 2014-07-26
Boot repair did not work. I tried with the "recommended options". No error messages during process.

Paste is: [http://paste.ubuntu.com/7864179/](http://paste.ubuntu.com/7864179/)

I am a little at a loss here&#8230;. I tried booting in UEFI and Legacy mode. Nothing.

---

### Post by oldfred on 2014-07-26
With one system installed you do not see grub menu normally. With BIOS you hold shift key until menu appears & with UEFI you hit escape key to get grub menu to appear.

You have a UEFI install, but have grub also installed in the MBR. Generally you only install in one mode or the other although you can modify a system to boot in both modes if gpt partitioned and hardware is UEFI capable.

You also have a separate /boot partition which normally is not required for most desktops. Server type installs with LVM or RAID may need a separate /boot. But often grub reinstall options skip or only mention as a footnote a /boot partition in the reinstall instructions. You must include your /boot with any reinstall of grub or other fixes.

Your sda1 now says it is FAT16?? The default is FAT32, but I believe FAT16 is valid, but intended for external devices. Did that get changed and then may indicate an issue with your efi partition. I might fully backup efi partition. Delete it and recreate a FAT32 version with gparted. Copy backup efi files back into it.

Before had you run Boot-Repair fixes?
Sony's only want to boot Windows and seem to have hard coded UEFI to only boot the Windows entry. You still have a Windows entry in UEFI, but no Windows folder in the efi partition.

It might just be easier to create a /efi/Microsoft/Boot folder and put grubx64.efi into that folder and rename it to bootmfgw.efi. Then you boot the Windows entry but it actually is grub.

Typical structure in efi partition.
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu


I thought both Ubuntu or Windows created the /efi/boot folders, but now see some systems without it.

From live installer mount the efi partition on hard drive:
       mount /dev/sda1 /mnt
cd /mnt/efi

us ls to see if created correctly
ls -l
mkdir Microsoft
mkdir Microsoft/Boot

      
 cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi

---

### Post by Sieges on 2014-07-26
Thank you for the extensive reply.
I tried renaming and copying the [COLOR=#000000]grubx64.efi but that trick did not work. I rebooted into LiveCD to confirm that the file was there. After this I ran Boot-Repair again. No success. Log is at [https://paste.ubuntu.com/7866559](https://paste.ubuntu.com/7866559)

After having "unfixable" issues upgrading Saucy to Trusty, i decided to do a clean install. Wiping all parities including the EFI and Windows 8 Rescue drive. I followed a "guide" as to what how to rebuild the file system (I do not have the link handy, sorry..). I said that having a seperate /boot was good incase you decided to LUKS encrypt the boot later. It also stated FAT16 for the EFI boot. I do not know HOW i fixed the Trusty boot issue (still prevailing after the clean install) but i was a manual hack. I used boot repair when first installing saucy to fix the grub (then I had both Win8 and Ubuntu installed)

I did not know that Sony had "hardware forced" windows booting. If i had known, i would not have bought the laptop.

Anyway, not that I am stuck with the laptop. Any suggestions?[/COLOR]

---

### Post by oldfred on 2014-07-26
You converted link to security link https which does not work.
[http://paste.ubuntu.com/7866559/](http://paste.ubuntu.com/7866559/)

If you have instructions saying FAT16 they are very old and wrong. FAT16 is optionally specified in UEFI instructions for removeable smaller devices. FAT32 is for all internal devices and larger external that have room for the larger size partitions that FAT32 supports.

Unless installing with LUKS now I would not use a /boot. But as long as you understand the extra complications on repairs and do the regular maintainance to prevent it from filling up, you should be ok.

This is what other Sony users have done.
  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
With encryption but you do not have to
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

---

### Post by thibault3 on 2014-07-27
I also have a Sony Vaio, all I had to do to fix the grub was make sure the secure boot was off, did you check that? 
Sorry if I am not so extensive or experienced, it just worked for me.

---

### Post by Sieges on 2014-07-27
Secureboot was off. I tried boot-repair with both SecureBoot on and off.
Ended up installing 14.04 again using this guide ([http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)). Booted on first attempt. No need to run boot repair

Anyway, I thank you for your help in this matter.

---

