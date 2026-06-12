---
title: "Dual booting Ubuntu 16.04 and Win8.1, Grub error: cannot load image"
date: 2016-04-28
forum: General Help
---

### Post by jared38 on 2016-04-28
Hi, I'm relatively new to dual-booting, and I'm having an issue with Grub not wanting to boot Windows.
So I'm trying to dual boot Ubuntu 16.04 (started as 15.10, upgraded to 16.04, but this issue happened before the upgrade) and Win 8.1 on my Lenovo Ideapad z585.
Booting to Ubuntu via Grub works perfectly fine, however, selecting the "Windows boot manager" option gives an error, and will not boot to it. However, if I boot straight to Windows via the boot selector (for lack of better term, what allows me to select a cd/usb/ubuntu/windows boot item before Grub), it works perfectly fine.
Both OS's otherwise work perfectly normally.

The error is as follows:
"/EndEntire
file path: /ACPI(a0341d0,0)/PCI(0,11)/ATAPI(0,0,0)/HD(2,96800,32000,5a5515f0367bc34b,2,2)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.

Press any key to continue..."
Pressing a key takes me back to the Grub menu.
This is the process I took to set the laptop up (it didn't seem to want to boot from my USB, so I used 2 of the thousand DVD's I have around):
Downloaded and burned Windows 8.1 ISO to R/W DVD (from media creation tool) via Imgburn (from my desktop)
Downloaded and burned Ubuntu 15.10 ISO to a different R/W DVD via Imgburn (from my desktop)
Booted laptop from Windows ISO, chose custom installation, set a 750gb (roughly) partition, and installed Windows to it (leaving roughly 200gb for Ubuntu after all was said and done)
Made sure Windows worked; it did
Booted laptop from Ubuntu CD, chose "Install alongside Ubuntu", and didn't change anything else.
Made sure Ubuntu worked, it did.

And that's when the problem happened; Grub won't boot to Windows.
I'd rather not redo everything, as I've set up quite a bit in Ubuntu; that'd be a last resort.
Is there something that I can do to fix this, or do I just need to reformat and reinstall?
Thank you for any help!

---

### Post by oldfred on 2016-04-28
How you boot install media for both Windows & Ubuntu is the boot mode it installs in, either UEFI or BIOS.
Did you install both systems in same boot mode?
UEFI & BIOS are not compatible. You can only switch from UEFI. Or once you have started booting into grub, grub cannot boot any other system not installed in same boot mode.
You can boot from UEFI/BIOS or one time boot key often f10 or f12 as UEFI is also a boot manager. Grub is both a boot manager (menu) and the boot loader for Linux.

If Windows is UEFI, so drive is gpt, then Boot-Repair can convert a BIOS Ubuntu install to UEFI boot by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI) using advanced mode.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jared38 on 2016-04-29
Thanks for the reply
They were both installed in UEFI.
This is my BootInfo report: [https://paste.ubuntu.com/16123672/](https://paste.ubuntu.com/16123672/)

---

### Post by oldfred on 2016-04-29
I do not believe grub can boot Windows when Secure boot is on.
Something about the chain of trust.

Have you tried with Secure boot off?

---

### Post by jared38 on 2016-04-29
Ah, never occurred to me that secure boot would affect it!
Yes, it works perfectly fine now, thank you oldfred!

---

### Post by Cavsfan on 2016-04-29
> **jared38 said:**
> Ah, never occurred to me that secure boot would affect it!
Yes, it works perfectly fine now, thank you oldfred!

Sweet! Glad you got it fixed. Yes oldfred knows his stuff about dual booting Windows and Ubuntu.
I'm dual booting Windows 10, Ubuntu 16.04 LTS and Arch Linux myself.

Don't forget to mark your thread as "solved" by going to the first post and clicking **Edit Post** and then click **Go Advanced**. 
At the top change the **Prefix** to **SOLVED** then click **Save Changes** and done.

Welcome to the forums! :smile:

---

