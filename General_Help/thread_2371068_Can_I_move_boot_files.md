---
title: "Can I move boot files?"
date: 2017-09-10
forum: General Help
---

### Post by willymiller on 2017-09-10
I created a bootable USB stick.  It works fine on a newer Dell PC.  When I tried it on an older Dell (Inspiron 530S), it will not boot.  After some research and testing, I believe the problem is a combination of the Inspiron BIOS (it has been updated) as well as how the USB stick was formatted.  The Unbuntu stick shows up in the boot menu on the Dell Inspiron as USB-ZIP0.  I have another USB stick that was formatted differently (both are FAT32), and it shows up as USB-HDD, and will boot fine.

I spent a good bit of time creating the Unbuntu USB stick and am not sure that I can recreate it very easily.  

Here is my real question.  I would like to copy all of the Unbuntu files (including boot files) from the original USB stick to the USB stick that will boot on the Inspiron, but I don't know a way to do that.  I tried a tool that creates an image (similar to an ISO), but when I did the copy, and then tried to boot, it showed up as USB-ZIP0 and would not boot (before the copy, it would boot as USB-HDD).

Is there a way to copy the boot files from USB 1 to USB 2, but still maintain the formatting?

Thanks.

---

### Post by lammert-nijhof on 2017-09-10
You could use the command line and the DD command:
> dd if=/dev/sd*X* of=/dev/sd*Y* or use GUI and the Disks Utility, in the menu there are options for create and restore disk image.

---

### Post by oldfred on 2017-09-11
Does Inspiron 530S have nVidia?
If so are you also adding nomodeset when booting?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

