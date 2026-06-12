---
title: "Grub Help"
date: 2015-05-18
forum: General Help
---

### Post by bob136 on 2015-05-18
I originally had only windows 8.1, then added windows 10, and third installed ubuntumate.  When I first turn on the computer it goes to the Grub Boot menu.  The options say Windows Boot Manager (on /dev/sda2), Ubuntu, Advanced options for Ubuntu, and System setup.  

Loading Ubuntu from the menu works fine.

When I try to load Windows Boot Manager, I just get an error.  

"EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/Sata(0,0,0)/HD(2,1f4800,82000,b04e33b2fae28848,2,2)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire error: cannot load image."

If I just press escape and type exit it will go to a bios like boot menu, it just lists ubuntu and Windows Boot Manager, and that seems to work fine.

Is there a way to fix grub so that it can correctly boot to the windows boot manager?  Or just remove grub and have windows boot manager be able to boot to ubuntu if I want to?

---

### Post by grahammechanical on 2015-05-18
Load into Ubuntu and open the terminal and enter this command

```
sudo update-grub
```

Does the printout show that Windows 8 and Windows 10 boot loader has been detected?

Regards.

---

### Post by bob136 on 2015-05-19
Here is the output of that command:

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Adding boot menu entry for EFI firmware configuration
done

---

### Post by QDR06VV9 on 2015-05-19
> **bob136 said:**
> Here is the output of that command:

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Adding boot menu entry for EFI firmware configuration
done
Hi bob 136 
This can be tricky thing to fix but see this thread it is long read but worth while.
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
Kind Regards

---

### Post by oldfred on 2015-05-19
When you press escape are you back at UEFI boot menu? 
Are both Windows & Linux installed in UEFI boot mode? BIOS boot mode is not compatible, and you do have to reboot if not in same boot mode.
Is either of the Windows still hibernated or has fast startup setting on? You must have it off and Windows fully shutdown for it to boot from grub menu in UEFI mode.
For whatever reason Windows boots the bootfgw.efi from UEFI ok when hibernated but not when called from grub.

---

### Post by bob136 on 2015-05-19
Sorry to bother you, I just changed the boot order in the bios to boot from the windows boot manger first.  Now it will have me choose between 8 and 10 normally, and If I want to do ubuntu I just press f12 on startup and it will let me boot into ubuntu with no issue.  It's not perfect, but I think it works pretty well.

If you're at all curious, I did run the Boot-Repair program: [http://paste.ubuntu.com/11228489/](http://paste.ubuntu.com/11228489/)
It didn't seem to fix the issue, just added more entries into grub.

I do have secure boot, OS optimized defaults, and uefi only enabled, maybe that was part of the problem, but I'm happy with the solution I've got.

---

