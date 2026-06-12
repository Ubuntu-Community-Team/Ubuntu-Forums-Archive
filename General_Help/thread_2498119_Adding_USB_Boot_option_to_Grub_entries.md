---
title: "Adding USB Boot option to Grub entries"
date: 2024-05-31
forum: General Help
---

### Post by albertramsbottom on 2024-05-31
I have a bootable Kali Linux on a USB Stick and thought I had set my bios to boot from USB first. But it doesn't work. Now I also dual boot using Grub with Windows 11 and Ubuntu. I wanted to check my bios to see if I had actually set to boot from USB first but it appears in my stupidity that at some stage I set a Bios password which I have forgotten

As I said I am fairly certain I have set USB boot and if so Grub seems to be the first boot option. I think I need to check the bios but cant and/or add boot kali from USB to Grub. so this is Grub/Ubuntu question

Any ideas where to start? So this is a Grub/Ubuntu question

Tricky I know

---

### Post by jeremy31 on 2024-05-31
If Ubuntu is installed using UEFI, check in terminal ```
efibootmgr
```

---

### Post by albertramsbottom on 2024-05-31
Sorry windows terminal or Ubuntu? And would I add to Grub and would this be huge security issue?

Thanks

---

### Post by jeremy31 on 2024-05-31
Ubuntu terminal

---

### Post by oldfred on 2024-05-31
Some examples.
Use labels:
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902](https://ubuntuforums.org/showthread.php?t=2076205&p=13783902#post13783902)
Configfile
[https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092](https://ubuntuforums.org/showthread.php?t=2076205&p=13788092#post13788092)

Note that an external drive may change order in UEFI/BIOS/grub. My sdc drive becomes sda on reboot. It depends on which drive I boot from.
I sometimes while booting have to use the edit function in grub to change a hd1 to hd0 or hd2.

You really need to resolve UEFI password issue. Otherwise you may end up with a brick, door stop, boat anchor, etc.

---

### Post by currentshaft on 2024-05-31
If all else fails, usually a CMOS reset will get your BIOS back to factory settings, removing any passwords.

---

### Post by albertramsbottom on 2024-05-31
Thanks I will look at this in the morning.

Is it not a security issue to add a USB option to Grub?

I will see if I can remember the UEFI password but as I stated think I already set to boot from USB first, perhaps Grub needs longer to recognise a USB or the USB needs longer before Grub loads

Thanks

---

### Post by tea for one on 2024-05-31
You do not add "USB option" to your internal Grub menu.
Booting from external USB device is controlled by your PC UEFI settings.

Although, you have set (and forgotten) your UEFI (BIOS) password, this should not prevent you from access to your PC boot menu.
The dedicated key depends on the PC manufacturer (e.g. F10 for Intel, F9 for HP, F12 for Lenovo etc.)

---

### Post by yancek on 2024-05-31
It isn't clear to me from your posts what your Kali is.  Did you do an actual install of Kali to a USB external drive or a usb/flash drive?  If it an install then you should simply be able to update-grub to add a menuentry.  If you have an EFI partiiton on the USB, you might be able to chainload it from your install Ubuntu grub.cfg file with a proper menuentry similar to the EXAMPLE below.   You would obviously need to change the fs-uuid entry to whatever it is on your usb and change the path on the chainloader to point to the Kali EFI boot file.  If it not EFI that will obviously not work.  

> menuentry 'Chainload KALI EFI'{
search --no-floppy --set=root --fs-uuid BF83-4862
chainloader /EFI/pclinuxos/grubx64.efi
}


---

