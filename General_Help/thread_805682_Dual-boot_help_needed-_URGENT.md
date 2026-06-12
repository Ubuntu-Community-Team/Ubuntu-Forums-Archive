---
title: "Dual-boot help needed- URGENT"
date: 2008-05-24
forum: General Help
---

### Post by Treeh on 2008-05-24
Hi,

I just installed Ubuntu...first Linux OS- I've ever used..anyway, I was following this guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Once I finished installing Ubuntu, I restarted and I expected to be presented with the GRUB menu...but wasn't. I just booted directly into Ubuntu.

How can I get the GRUB menu to show up so I can boot back into XP?

Thanks.

-Also-

I have a Siemens USB Stick 108 Wifi USB adapter...how do I go about installing this? Thanks.

---

### Post by cdtech on 2008-05-24
How did you install Ubuntu, on a partition of the primary or on a second drive?

No matter:

(Within Ubuntu open a terminal and issue this command:)
sudo grub

This will put you in a GRUB shell >

type:
grub> **setup (hd0)**

This will set the GRUB bootloader to the MBR of the first drive in your scheme or the primary hard drive.

Hope this helps.......

---

