---
title: "[lubuntu] DD mode imaged USB live, how to pass a grub CMDLINE?"
date: 2019-08-07
forum: General Help
---

### Post by nicsure on 2019-08-07
Hi, I have an issue with installing Lubuntu onto a Dell Thin Client Z90D7. It seems as though the EFI NVRAM is over 50% full and the grub installer cannot write the boot entry to the EFI (paranoia). I've searched for a bunch of solutions and only one of them will appear to work. There is no secure boot enabled, the NVRAM is not flagged as read-only, there are no dump files in the NVRAM to delete, I've manually removed all previous EFI boot entries in the UEFI and cleared the CMOS using the internal jumper. None of those options work at all. I cannot update the BIOS as this is no longer possible to do with the software supplied by Dell, although it is supposed to update the BIOS while installing the latest Windows 7 Embedded, it unfortunately does not work and the installer just skips that part. The current BIOS of the unit is 2.0C

The only solution left to try was to boot the system with an added cmdline to grub called 'efi_no_storage_paranoia' which prevents the check for the NVRAM usage. My issue is that I can't seem to figure out how to do it. When the USB media boots, I get no grub menu, pressing keys, holding shift and all the usual stuff will not bring up any menu. The screen goes black once the booting starts, stays black for about 30 seconds, then the USB keyboard and mouse power down, come back up, then the Lubuntu desktop appears. I've done this a whole bunch of times, each time trying different keys but I cannot get any grub menu to appear in order to apply the cmdline.

As a test to see if this (NVRAM usage) was only an issue with Lubuntu, I also installed Arch Linux in EFI mode. When installing grub, I get the same error as with Lubuntu, that there is no room on the EFI NVRAM, so this wasn't an issue with Lubuntu, but with my Thin Client. Arch Linux's live media (again prepared with DD and booted as EFI), does show a grub menu and I was able to include the 'efi_no_storage_paranoia' cmdline. After doing this and trying grub install again, it worked, the boot var was created and Arch booted with no issues. So once I knew that was the solution I came back to Lubuntu and tried to figure out how to activate this boot option, and have had no luck at all so far. Hence this post. Any help would be greatly appreciated.

Cheers
Marc

EDIT: Forgot to mention, installing Lubuntu 19.04

EDIT2: Apparently, this problem of no grub menu only happens when booting using the UEFI boot menu (pressing p during POST), if I set the boot order such that the USB stick just boots by itself and press F6 while booting, the grub menu will then appear. I can then press 'e' on the menu option and add the option to the linux cmdline. So all sorted now. From what I can gather from various sources on this unit, the BIOS is notoriously buggy. I cannot be sure, but I think what's happening is that the BIOS is reporting the size of the NVRAM area to be zero. Since it's supposed to be used with Windows 7, and the Windows 7 install does not check for NVRAM usage, they probably thought it wasn't needed and didn't implement it, just filling the interface requirement by returning a zero. Hence stuff that does check the NVRAM usage will always report it as full.

---

### Post by VMC on 2019-08-07
You might want to review efi.
```
efibootmgr
```
To see where you stand in regards to boot order.

---

