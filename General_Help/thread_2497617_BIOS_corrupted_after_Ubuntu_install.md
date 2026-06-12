---
title: "BIOS corrupted after Ubuntu install"
date: 2024-05-12
forum: General Help
---

### Post by emanuelekk on 2024-05-12
Hello everyone! I'm really desperate as I think my laptop is now broken, so please help if you can!
I tried to install Ubuntu (actually it was Lubuntu, but I think the boot part should be the same) and I think now my BIOS is corrupted. here is what happened:
Decided to install Lubuntu on an ASUS K550V laptop. I also wanted to change the hard drive to an SSD one.
I removed the old drive with windows and installed the SSD, inserted a USB drive with the Lubuntu image and the installation goes smoothly.
I click on "finish" and the computer restarts, it shows the ASUS logo along with "powered by Lubuntu". Here starts the problems: It gets stuck on this screen, and after almost an hour I force the shutdown by pressing the power button.
Now whenever I start the laptop it goes straight to the BIOS page and no matter what I try, it won't boot and just goes to the BIOS page. Here is what I tried so far:
- Restore the bios to default setting and boot
- Manually add a boot option: it let me select an EFI file (so it can read the SSD), I tried shimx64.efi. Save and restart and it still goes straight to BIOS. Also the boot option I added is gone.
- Disable Secure boot and fast boot and manually add a boot option: this time I selected grubx64.efi but as before nothing happened and the option is gone after restart.
- Tried to change the time setting to see if it wasn't saving my changes: It kept the change, so it is saving.
- Insert the USB drive I used to install Lubuntu to try to reinstall it: nothing
- Manually add a boot option to boot from the USB drive
- Put back the original hard drive with windows, restore the BIOS to the default settings
- Put back the original hard drive with windows, Manually add a boot option and select the windows efi file.

I run out of ideas of what I can do. Is it possible that the install corrupted my BIOS?
How can I fix it?

Thanks in advance

---

### Post by TheFu on 2024-05-12
> **emanuelekk said:**
>  
I run out of ideas of what I can do. Is it possible that the install corrupted my BIOS?


No. Ubuntu installs don't touch the BIOS.  Download a fresh BIOS (perhaps an upgrade) from the motherboard vendor and install that using the MB vendor instructions, then try booting into _Try Ubuntu_  mode from the ISO.

Is the firmware on the SSD current?  Update is from the vendor's firmware.

Also, did you validate that the ISO file for Lubuntu was correct, uncorrupted?

Also, which LUbuntu version?  I've installed Lubuntu 24.04 3 times in the last 2 weeks.  No unexpected problems with it that I've experienced.

---

### Post by emanuelekk on 2024-05-12
Updated the BIOS and booted up immediately!   :guitar:

Thanks!

---

### Post by dragonfly41 on 2024-05-12
Solved .. ok. I see you did that.

---

