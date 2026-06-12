---
title: "Creating Ubuntu ISO for UEFI"
date: 2018-06-19
forum: General Help
---

### Post by lizard2014 on 2018-06-19
Hello. I am building my own customised version of Ubuntu 16.04 by following the steps provided here: [https://nathanpfry.com/how-to-customize-an-ubuntu-installation-disc/](https://nathanpfry.com/how-to-customize-an-ubuntu-installation-disc/)
The problem is that the customised ISO doesn't boot in UEFI mode (not sure about BIOS). Is there something missing in the last command (genisoimage command) in the linked tutorial?

---

### Post by perryhelionsemail on 2018-06-19
Hi lizard2014 - I'm not sure how useful this is, but I was following an old guide to repairing grub on a machine using a Live USB ([https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd))

I'd used it before and it worked fine, but that was to repair a standard Legacy boot install and unfortunately the guide made no reference to using UEFI (I think it was written before UEFI was widely used) but I got it to work with UEFI by adding an extra line.

The main instructions use

sudo mount /dev/sdXY /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo chroot /mnt

Which is doing something very similar to the Customize An Ubuntu Installation Disc tutorial. i.e mounting some useful parts of the system in a particular directory ( /mnt in this case).

Once you are in the chroot, with the useful partition mounted (/dev/sdXY) and also /dev, /dev/pts, /proc and /sys you can just run grub install /dev/sdXY (/dev/sda in my case) to get grub installed on that disk.

It didn't work with UEFI until I added 'sudo mount /dev/sda2 /mnt/boot/efi' after the first 'sudo mount /dev/sda7 /mnt' line, so I get the feeling that you'll need to do something similar when you are making your customised Ubuntu Installation Disc.

My best guess is that you need something like 

mount -t boot none /boot

or 

mount -t boot/efi none /boot/efi

once you are in the chroot.

It might be worth a try, but I'm not familiar enough with using chroot to know for sure - it just seems to be a similar process that looks like it needs you to have /boot/efi mounted before you start adjusting your system image.

(If it does work, then don't forget to unmount it when you're unmounting the other bits later)

---

### Post by oldfred on 2018-06-19
BIOS boot with Ubuntu uses syslinux boot loader.
But UEFI boot with Ubuntu live installer uses grub. And all UEFI systems boot from /EFI/Boot/bootx64.efi. The installer has a version of grub for use with installer and is renamed to /EFI/Boot/bootx64.efi.
If you only want UEFI boot, you do not need to directly install boot loader, just copy files.
       UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) 

I have fast Internet and just find it easier to run scripts after install. I use LTS version as main working install, but typically have multiple other installs. And was manually updating. But after a few times doing same thing, I said is that not what computer is for. I copied commands from history into bash file and removed sudo.
       scripts instead of custom ISO
[https://ubuntuforums.org/showthread.php?t=2394463](https://ubuntuforums.org/showthread.php?t=2394463) 

I have installed the UEFI version of grub to a flash drive directly (-removable), but have to create my own grub.cfg in ESP and grub.cfg in the /boot folder. I have only used this to directly loopmount ISOs on a flash drive.

---

### Post by lizard2014 on 2018-06-23
I wonder how the original Ubuntu ISO is built. Because it can boot in all conditions. Does anyone know?

---

### Post by oldfred on 2018-06-23
To make it UEFI bootable all they did was add an ESP - efi system partition which for installer is the entire installer. UEFI only boots from an ESP FAT32 with boot flag and from /EFI/Boot/bootx64.efi. They then make a slimmed version of grub as bootx64.efi as it only has to boot live installer.
You can open the ISO with the iso mounter and see the structure.

You can install grub in UEFI boot mode with removable parameter in grub-install command.

These were my commands to install grub to a flash drive labeled MC4GB. I then manually created a grub.cfg to boot my ISO directly.

       610  sudo mkdir /media/fred/MC4GB/EFI
  611  sudo mkdir /media/fred/MC4GB/EFI/BOOT
  612  sudo grub-install --target=x86_64-efi --boot-directory=/media/fred/MC4GB/EFI/BOOT --efi-directory=/media/fred/MC4GB --removable
 621  sudo grub-install --target=x86_64-efi --boot-directory=/media/fred/NEWEFI_32MC4GB/EFI/BOOT --efi-directory=/media/fred/NEWEFI_32 --removable
sudo grub-install -v --no-floppy --boot-directory=/tmp/usb2 --efi-directory=/tmp/usb2 --removable --target=x86_64-efi /dev/sdX

---

### Post by lizard2014 on 2018-06-29
That is one workaround, but there must be a way to create a hybrid ISO which when burnt to a DVD, makes a hybrid installation medium (BIOS+UEFI). I remember that this functionality is available in oscdimg tool provided for windows (where you specify both BIOS and UEFI boot image path in the command), but I don't know how to do this in genisoimage. How does Canonical make hybrid ISO? Or do they use xorriso?

---

### Post by oldfred on 2018-06-29
Ubuntu ISO just has two different boot loaders. 
It uses syslinux for BIOS boot.
And it uses grub for UEFI boot.

Do not know how they create ISO, but that would indicate they just install two different boot loaders, separately.

---

### Post by C.S.Cameron on 2018-06-29
Mkusb makes a Live or Persistent flash drive that boots either BIOS or UEFI.
What seems to work for me is boot the flash drive in BIOS if you want to install a BIOS system and boot the flash drive in UEFI if you want to install a UEFI system on the HDD.
My experience is limited wrt UEFI.
Mkusb only uses grub, no syslinux.

---

### Post by oldfred on 2018-06-29
In grub manual is this section.
[www.gnu.org/software/grub/manual/grub/grub.html#Configuration](www.gnu.org/software/grub/manual/grub/grub.html#Configuration)

 **[B][FONT=arial]4.2 Making a GRUB bootable CD-ROM[/FONT]**[/B]

Which is more for making a grub rescue image.

---

