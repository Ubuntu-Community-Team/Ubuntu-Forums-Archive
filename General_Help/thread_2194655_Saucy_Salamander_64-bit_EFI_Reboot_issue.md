---
title: "Saucy Salamander 64-bit EFI Reboot issue"
date: 2013-12-19
forum: General Help
---

### Post by Melon Head on 2013-12-19
Using 64-bit UEFI booting on Sauce Salamander I have noticed that rebooting does not work.  The screen just goes black and the computer hangs. 

I looked around google and I found this fix for the issue: 

Edit /etc/default/grub and look for the line GRUB_CMDLINE_LINUX=""

Change the line to read GRUB_CMDLINE_LINUX="reboot=efi"

Save the file and then do sudo update-grub

Shut the system down and then after that it will work just fine. 

My question is this: Why does this fix it?  Grub is a boot loader, what does booting up have to do with shutting down?  Why would modifying the GRUB configuration affect rebooting at all?

---

### Post by oldfred on 2013-12-20
I have not seen anything related.

But grub does modify its boot, if you do not have a normal shutdown. It will always show a menu even if you have configured not to show menu, so you can go into recovery mode if desired.

There also are a lot of improvements with each update of Ubuntu to UEFI as it is changing/fixing lots of issues, so I would expect 14.04 to have even more changes.

---

