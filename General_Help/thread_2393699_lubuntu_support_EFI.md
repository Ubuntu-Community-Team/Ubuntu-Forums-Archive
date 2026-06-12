---
title: "lubuntu support EFI?"
date: 2018-06-06
forum: General Help
---

### Post by anand31 on 2018-06-06
Hello friends,
   i wanted to install a lightweight ubuntu based distro , i found lubuntu to be the choice. my harddisk is GPT  partition style . i created the usb image using dd .when i boot i see no efi device to boot from , i was wondering if lubuntu support EFI. any links would be great ..

Thankyou .

---

### Post by QIII on 2018-06-06
Moved to General Help.

Lubuntu is an official flavor of Ubuntu, so your post did not belong in the Other OS area.

Cheers!

---

### Post by oldfred on 2018-06-06
All flavors support UEFI boot.
But you choose to boot with UEFI from UEFI.

Many systems have separate setting to allow USB boot. When secure boot is off, it may allow BIOS only USB boot, but if UEFI on and even if Secure Boot is off, it may need a setting to allow USB boot.

What brand/model system?
What video card/chip?

---

### Post by anand31 on 2018-06-06
thanks oldfred for the reply,

i have Lenovo Ideapad Bseries(B50-70), ATI Radeon 8500M video chip. You are absolutely right about the BIOS SecureBoot settings, But what i wanted to know when i copy the lubuntu.iso to USB and when i boot with the USB, the usb should show as EFI device in bios , it doesn't !. coz earlier i tried linux mint , Ubuntu using dd method. they all show up as EFI device .. but this doesnt .hence the doubt . anyways when i still go ahead and select the usb device to boot , just the cursor blinks in the top left. i waited for 5 - 10 mins but nothing happened coz in some posts in this forum i saw people saying they were experiencing slow boot time before installation and after installation. i want the usb device to be detected as EFI . 

update: - dropped my plans to install lubuntu ... going back to Ubuntu Mate. 


thankyou.

---

### Post by lawrence32 on 2018-06-06
You can create a Ubuntu USB with EFI bootloader using the freeware [Rufus]("https://rufus.akeo.ie/") or [ISO2Disc]("https://www.top-password.com/iso2disc.html"). While creating the USB, you need to choose the GPT partition table. If your USB drive is formatted with MBR partition table, it won't be recognized as EFI bootable device.

---

### Post by anand31 on 2018-06-07
thanks lawrence32 ,
    this sounds promising is there a  equivalent linux tools to do this.can i try gparted for creating efi device?

---

### Post by oldfred on 2018-06-07
Lots of info on USB boot for installing
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick

      [/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
    
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

---

### Post by sudodus on 2018-06-07
**Lubuntu 64-bit iso files can [be cloned to USB/DVD drives that] boot in UEFI mode as well as BIOS (legacy) mode**, but Lubuntu 32-bit iso files can boot only in BIOS mode unless you use some tool, that provides UEFI capability, for example mkusb (for persistent live drives using usb-pack-efi).

**This is true not only for Lubuntu but for standard Ubuntu and all Ubuntu community flavours** (Kubuntu, Ubuntu Budgie, Ubuntu MATE, ...Xubuntu).

Edit:

- If you boot into your USB/DVD drive in UEFI mode, and run the installer, it will install in UEFI mode.
- If you boot into your USB/DVD drive in BIOS mode, and run the installer, it will install in BIOS mode.

There are automatic options, where the EFI partition, the root partition (and maybe a swap partition) will be created. But you can also create them with gparted and specify what you want with 'Something else' at the partitioning window of the installer.

---

