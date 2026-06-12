---
title: "Help with Boot repair"
date: 2017-02-17
forum: General Help
---

### Post by alanpatx on 2017-02-17
Hi, I am running Ubuntu 16.04 on a 64-bit PC. No other operating systems. I accidentally deleted the boot partition with gparted (/dev/sda1), thinking I was erasing a partition on an SD card, then realised my mistake. I have created a USB 16.04 install key & have booted to a live distro on that, installed the boot-repair utility and have been trying to use that to restore the partition. My BIOS is set to UEFI. The size of the partition I deleted is 94MiB located at the start of the disk. I recreated a FAT32 partition in that sector (i think it was FAT32 originally bit I'm not 100% sure). I tried setting the boot flags to boot/esp, I get "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.". So I tried erasing the sda1 partition again & creating an unformatted partition. GParted doesn't seem to like this idea and automatically marks it as FAT32. I get the same message. My main distribution files are in /dev/sda2 with one other swap partition (/dev/sda3). The /dev/sda2 partition contains a /boot directory with kernel & grub files. I have tried various combination of bios-grub/boot/esp flags on sda1 & sda2, but I'm going round in circles & don't really know what I'm doing, so help would be appreciated. Also tried changing the PC bios from UEFI to legacy, but that didn't seem to make a difference, so I changed it back. PC still does not boot. I have created a boot-info report available to view at: 

[http://paste2.org/1nzYBYG6](http://paste2.org/1nzYBYG6)

Thanks,

Alan

---

### Post by oldfred on 2017-02-17
New UEFI systems have two ways to boot, UEFI or CSM(BIOS).
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
And UEFI uses as default the newer gpt partitioning over the 35 year old MBR(msdos) partitioning.

With UEFI you must have the ESP - efi system partition which is the FAT32 with esp/boot flag.
But with BIOS boot, you must have a bios_grub partition for grub to correctly install to the protective MBR when using gpt partitioning.

So if Boot-Repair is asking for  a bios_grub partition you are installing in BIOS boot mode.
How you boot installer, UEFI or BIOS is how it installs, UEFI or BIOS and how it repairs (normally).

So if you want UEFI boot, make sure you have the FAT32 ESP and boot the Ubuntu installer in UEFI mode from UEFI, add Boot-Repair and in its advanced mode run the full uninstall/reinstall of grub. That uninstalls grub-pc (BIOS) and installs grub-efi-amd64(UEFI).
Or if you want BIOS boot make sure you have a 1 or 2MB unformatted partition with bios_grub flag and boot Ubuntu in BIOS mode and run the full uninstall/reinstall of grub.

You now have copy of grub in MBR. UEFI may offer to boot it but it will not work, unless you add bios_grub partition and reinstall grub.

Your fstab shows the mount of the efi partition commented out, so it looks like last reinstall of grub was in BIOS mode. Reinstalling in UEFI mode will add a new entry in fstab to mount the ESP/efi partition.

What brand/model system? Some violate UEFI spec and boot in UEFI mode using description. And only valid description is "Windows Boot Manager". We have many work arounds for those systems, depending on configuration. See also link in my signature for lots more info.

---

### Post by alanpatx on 2017-02-17
Thanks for getting back to me & for the explanation.

The BIOS in the PC has always been set to UEFI. The OS was originally installed that way so I'm fairly sure it was booting in UEFI mode previously.

Since your post, I tried turning off fastboot in the BIOS. Recreated the partition formatted with FAT32 & set esp/boot flag. I recreated the USB key using "MBR partition scheme for UEFI", previously it was created with "MBR partition scheme for UEFI and BIOS". Booted with that & installed boot-repair. Boot repair still gives me the above message requesting bios_grub flag. So I created the USB key again using the instructions [here]("https://ubuntuforums.org/showthread.php?t=2299040")

Unfortunately I'm still getting the same message requesting bios_grub flag.

I can't tell you much about the PC as it's a rebranded machine (Advent). CPU is Intel Core i5-3330, BIOS E7788IDO V3.0B9, memory 8192MB

---

### Post by oldfred on 2017-02-17
If reinstall of grub is asking for bios_grub that is BIOS boot of flash drive.

You should have two entries in UEFI to boot flash drive.
Usually one is clearly UEFI:name and other is just name which is then the BIOS boot.
Where name is a label or brand name of flash drive.

You may have to turn on allow USB boot in UEFI. 
My motherboard had allow USB boot and setting for UEFI & BIOS, but that only booted flash drive in BIOS mode. I had to change to UEFI only to get it to boot in UEFI mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The highlighted one is BIOS and one below is UEFI:

---

### Post by alanpatx on 2017-02-17
Mmm.. My motherboard has the following option for USB boot (attached). Seems to be set for UEFI boot.

---

### Post by oldfred on 2017-02-17
If you use that to boot, do you get grub menu or purple accessibility screen(BIOS)?

Boot-Repair may want to install in BIOS mode, if you do not have the ESP.
Or maybe if it does not see files in ESP /EFI/ubuntu or if fstab does not have mount of efi partition.

But if you have ESP, FAT32 with boot flag/esp flag and use Boot-Repair's advanced mode can you not totally uninstall grub and install grub-efi-amd64 for UEFI boot?

---

### Post by alanpatx on 2017-02-17
I don't get a grub menu. It drops to an EFI shell.

I'll resume this tomorrow. Time getting on here. Thanks.

---

### Post by alanpatx on 2017-02-18
I have the "Reinstall GRUB" option checked in boot-repair, but never gets that far as it asks for bios_grub. I tried running "sudo boot-repair -e " but it doesn't start, I get the following: [http://paste2.org/V6U5X2LZ](http://paste2.org/V6U5X2LZ)

I tried creating /home/usr/.config but get the same result, without the "cannot access /home/usr/.config" message. GUI doesn't start.

So... I tried reinstalling grub-efi-amd64 by using the instructions [here]("http://superuser.com/questions/376470/how-to-reinstall-grub2-efi") with chroot. Rebooted hopefully, but sadly it still just drops to an EFI shell. Here is my boot-info after carrying out the reinstall procedure:

[paste2.org/72YJjs3x]("http://paste2.org/72YJjs3x")

---

### Post by alanpatx on 2017-02-18
Aha! Sorted now. By running the reinstall procedure above with chroot, but using: sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi

[COLOR=#242729][FONT=Consolas]Up & running again. Thanks for your input.

Alan


[/FONT][/COLOR]

---

