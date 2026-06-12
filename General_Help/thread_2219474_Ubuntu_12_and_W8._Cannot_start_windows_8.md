---
title: "Ubuntu 12 and W8. Cannot start windows 8"
date: 2014-04-24
forum: General Help
---

### Post by claudiorv89 on 2014-04-24
Hi. I have a HP Pavilion 15-006. I have Windows 8 and Ubuntu 12. I deleted the windows rescue partition, I have it in a usb. Then I installed Ubuntu, with about 8 GB for /, 2 GB swap, and finally /home. Ubuntu works perfectly, but i can't enter in Windows. 

I have this:

Error: unkown command 'drivemap'
Error: invalid EFI file path

I used Boot-repair with the live-usb and I have this error:

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted  filesystem, bios_grub flag). This can be performed via tools such as  Gparted. Then try again. Alternatively, you can retry after activating  the [Separate /boot/efi partition:] option.

I tried both things and the problem continues. I have this link with the result:

[http://paste.ubuntu.com/7321180](http://paste.ubuntu.com/7321180)

I think I have a circus with the boot :D Thanks!

---

### Post by oldfred on 2014-04-24
Grub2's os-prober with 12.04 still finds only BIOS boot entries. This was fixed with 13.10 or later.
       grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Boot-Repair normally adds correct entries into 25_custom to chain load to the efi partition not directly to the Windows main partition like you would with BIOS.

      
 type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {

If it did not add entries, you can manually add correct entry to 40_custom. Examples in bug report above.

      
 gksudo gedit /etc/grub.d/40_custom


```
 menuentry "Windows bootmgfw.efi UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

    
```

---

