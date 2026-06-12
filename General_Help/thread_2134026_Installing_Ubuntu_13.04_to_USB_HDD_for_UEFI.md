---
title: "Installing Ubuntu 13.04 to USB HDD for UEFI"
date: 2013-04-09
forum: General Help
---

### Post by gearedandroid on 2013-04-09
hey guys, i've been trying to install the
[64-bit PC (AMD64) desktop image]("http://ubuntuforums.org/ubuntu-13.04-beta2-desktop-amd64.iso") from [http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

I install it to a usb thumb drive, i then enabled legacy support in the bios. I then rebooted and succesfully Installed ubuntu to my other usb drive, my 500gb HDD
When i tried to boot of the 500gb HDD it would just jump straight to windows 8? It's really weird! I hit F9 to manually choose a device to start from and it jumps to windows 8 when i select my drive.

This is really pissing me off! on the HDD do i need an EFI patition? This is how i was installing and what patitions i do (My usual patitions i have used before on other 64bit machines)
partion 1 - SWAP, 2GB
 partition 2 - Boot, 500mb 
 partition 3 - / ,200gb 
partition 4 - HOME, 97.5gb 

it's probably something really stupid. 
I'm using a Compaq Presario laptop - Windows 8

---

### Post by oldfred on 2013-04-09
If Windows 8 is in UEFI mode and you want to dual boot you need Ubuntu in UEFI mode. If one is UEFI and the other BIOS, you have to go into UEFI/BIOS and change boot mode. You cannot dual boot from UEFI or BIOS as each writes different data to hard drive for system to boot with. BIOS also uses interrupts, UEFI uses drivers not Interrupts.

IF drive is gpt partitioned Boot-Repair can convert install to UEFI boot, but all gpt bootable drive should have an efi partition as the first partition per UEFI standard (or second as that is usually Windows version).
Ubuntu will boot from gpt partitioned drives in either UEFI or BIOS mode. In UEFI you need the efi partition and in BIOS you need the bios_grub partition to get grub to install correctly.

If drive is MBR, you may be able to convert to gpt, but really have to have good backups and may have to make minor adjustments to partitions to get a conversion to work.

---

### Post by gearedandroid on 2013-04-10
So what, simplified steps to install it to the hdd and use it every now and then?
Do i just make an efi partition instead of boot or what?

---

### Post by oldfred on 2013-04-10
Is drive MBR or gpt.
If MBR it is a lot of work, but if you system is UEFI you really should not be using MBR for any drive you want or may want to boot from. You can boot Ubuntu if installed in BIOS/MBR by going into UEFI/BIOS and change to BIOS. Then when you want Windows go into UEFI/BIOS and change to UEFI. Not an easy way to dual boot.

If drive is gpt, Boot-Repair will convert and you probably can just use the one efi partition that Windows has. I prefer to make each drive independently bootable, so when Windows drive fails you can still boot Ubuntu drive. So I would suggest the efi partition on the Ubuntu drive also with Ubuntu's boot files. System will actually only boot from one drive and grub will chainload to another drive.

---

### Post by xtsuname on 2013-05-31
> **oldfred said:**
> Is drive MBR or gpt.
If MBR it is a lot of work, but if you system is UEFI you really should not be using MBR for any drive you want or may want to boot from. You can boot Ubuntu if installed in BIOS/MBR by going into UEFI/BIOS and change to BIOS. Then when you want Windows go into UEFI/BIOS and change to UEFI. Not an easy way to dual boot.

If drive is gpt, Boot-Repair will convert and you probably can just use the one efi partition that Windows has. I prefer to make each drive independently bootable, so when Windows drive fails you can still boot Ubuntu drive. So I would suggest the efi partition on the Ubuntu drive also with Ubuntu's boot files. System will actually only boot from one drive and grub will chainload to another drive.

Would you be kind enough to explain on how you installed the EFI partition on the Ubuntu Drive?
When I started bootrepair, the only EFI partition that seems to be found is the one that already exist in the computer, and that the EFI partition that I created in Ubuntu's Drive wasn't available.

Thanx

---

### Post by fantab on 2013-05-31
Only one EFI partition per Disk. If you have two Disks then you must have installed GRUB on the Disk on which Ubuntu is NOT installed. Boot-Repair has to be told in the Advanced optition where it has to install Grub, if grub was not installed in the ubuntu disk.

Post the output of 'BootInfo Summary' that Boot-Repair generates. It will be better if you start your own thread. For reference post the link of the new thread here.

---

