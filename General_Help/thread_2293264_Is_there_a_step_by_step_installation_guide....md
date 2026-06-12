---
title: "Is there a step by step installation guide..."
date: 2015-09-03
forum: General Help
---

### Post by nonsisa on 2015-09-03
how to full install Ubuntu on an USB stick for an UEFI system?

Has anyone actually ever succeeded in creating such an Usb stick?

I don't mean the bootable version with persistence mode.

Can anybody guide me through on how to do that on a 16GB Usb.

---

### Post by Ignacio_Tiraboschi on 2015-09-03
I don't understand whether you're trying to install Ubuntu on an HD with a 16GB USB stick, or if you want to actually boot Ubuntu from the stick.
I don't know if you have seen the [official Ubunu documentation]("https://help.ubuntu.com/community/UEFI").

But in any case, I managed to do a UEFI Ubuntu installation by:
1. Downloading a 64bit Ubuntu (because UEFI implies 64bit, I used 15.04 but 14.04.03 should be fine too)
2. Then (I assume you're using Windows) use [Rufus]("https://rufus.akeo.ie/") (Rufus has an option for an MBR partioned USB stick, you should use that for it won't be compatible with UEFI if it's not), wich is a software to make bootable USB sticks. You can also use [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button").
3. After that you should simply boot with the stick and have a UEFI installation. Just in case use your BIOS boot menu to choose UEFI and obviously have UEFI boots and stuff enabled on your BIOS config.

In case this doesn't work you should post some more information, I'm just assuming stuff.

---

### Post by oldfred on 2015-09-03
I do have a full install on my 64GB flash drive. 
I partitioned in advance with gpt partitioning.
I created both an ESP - efi system partition and a bios_grub partition, so I could boot either UEFI or BIOS, but used UEFI.
Install is just like any install to another drive, but grub only installs to the ESP on drive seen as sda.
Backup your ESP first. Every second install of Ubuntu has overwritten my main working install's efi partition. It turns out if same version of grub the only difference is the tiny 3 line grub.cfg in /EFI/ubuntu and the UUID it uses to find the full grub.cfg in your install.

Flash drives only boot from /EFI/Boot/bootx64.efi. And grub must see /EFI/ubuntu/grub.cfg.
So copy /EFI/ubuntu from sda to flash drive. Then copy again to /EFI/Boot and rename either grubx64.efi or shimx64.efi to bootx64.efi. 

Some related info, but for both BIOS & UEFI.
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
 Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

---

### Post by nonsisa on 2015-09-07
Ignacio_Tiraboschi thanks for your reply, but I wanted a full installation on an USB stick, wich is UEFI bootable. 

I allready have an Usb stick that is uefi bootable, where the Iso is on it.


The tipps from Oldfred are nice but till now I didn't succeed in completing the task.

---

### Post by nonsisa on 2015-09-07
I achieved it by the following method.
1 removing the hard drive
2 booting from uefi bootable usb
3 installing on another usb

---

### Post by nonsisa on 2015-09-09
There is still a problem. After I boot into Windows again, the stick won't work anymore. Any ideas, why this is?

---

### Post by sudodus on 2015-09-09
I suggest that you try according to the following links, where I describe a system that has survived for me. It has not yet been destroyed by Windows ;-)

[Stable_portable_systems_-_good_for_USB_sticks](https://help.ubuntu.com/community/Installation/FromUSBStick#Stable_portable_systems_-_good_for_USB_sticks)

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)

---

### Post by oldfred on 2015-09-09
Removing a drive often then UEFI forgets the entries it has to boot from that drive.
Not sure if a couple of reboots it auto finds them or if you need to manually create a new entry for Windows.

If your efi partition is sda1:
 New Windows entry - assumes default sda1,  add -p 2 if sda2 or -p 3 if sda3:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

More details on efibootmgr commands.

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by leunam12 on 2015-09-09
> **nonsisa said:**
> There is still a problem. After I boot into Windows again, the stick won't work anymore. Any ideas, why this is?When I had that exact same problem I solved it by disabling some Windows 8 options from the BIOS, I think it was fast boot and safe boot. Play a little bit with those settings and see what happens.

---

### Post by oldfred on 2015-09-09
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But it may be that you do not have /EFI/Boot/bootx64.efi on flash drive?
UEFI default boot from flash drive is always bootx64.efi on expected path of /EFI/Boot in the ESP - efi system partition.

---

### Post by nonsisa on 2015-09-19
> **oldfred said:**
> Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But it may be that you do not have /EFI/Boot/bootx64.efi on flash drive?
UEFI default boot from flash drive is always bootx64.efi on expected path of /EFI/Boot in the ESP - efi system partition.

No, that is not the case. I do have the /EFI/Boot/bootx64.efi on the flash drive. But still it won't boot from the usb stick.

---

### Post by sudodus on 2015-09-19
Can you make your computer boot from any USB pendrive (for example an Ubuntu live drive)?

In other words, is the problem booting at all from USB, or is the problem, that your installed system in the pendrive does not work?

---

### Post by nonsisa on 2015-10-14
The latter.
I do have a UEFI bootable pendrive functioning.

The problem is, I want to have a full installation on an USB drive working in UEFI mode.

The goal would be you plug in the USB, start the pc/laptop hit the Fwhatever Key to select the USB as bootdevice and then have a fully installed Ubuntu running on an USB.

I know this was possible in Legacy mode, so why is there no solution to have this working on an UEFI system?

---

### Post by oldfred on 2015-10-14
My full install to a flash drive boots in UEFI mode.

Is /EFI/Boot/bootx64.efi really the copy of shim from the ESP on sda?
Did you copy /EFI/ubuntu from ESP on sda to ESP on sdb (or flash drive), then copy again into /EFI/Boot so you can rename shim?
The grub in EFI/Boot still is hard coded to look for files & the grub.cfg in /EFI/ubuntu, so that must still exist. 

Post a link to Summary report from Boot-Repair. 
And post grub.cfg from the ESP in /EFI/ubuntu on flash drive as Boot-Repair does not include it.

---

