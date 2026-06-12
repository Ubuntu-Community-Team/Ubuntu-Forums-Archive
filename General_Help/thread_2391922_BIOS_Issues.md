---
title: "BIOS Issues"
date: 2018-05-14
forum: General Help
---

### Post by tororii on 2018-05-14
[FONT=arial]I am currently dual-booting Windows 10 and Ubuntu 18.04, and am having an issue with the GRUB menu loading. Every time I boot my computer, it boots straight to Windows. I used the boot repair tool, ran"bcdedit /set {bootmgr} path \EFI\ubuntshimx64.efi" and had no success. This is the pastebin I was given- [http://paste.ubuntu.com/p/cFsPQ9JxK8/](http://paste.ubuntu.com/p/cFsPQ9JxK8/)  . Currently, the only way I can get into Ubuntu is if I use the live USB and run "sudo efibootmgr -n 6" and then reboot. It works, but is really tedious to have to do that each time. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any advice/help? If you need any system info, I'll be happy to provide.[/FONT]

---

### Post by oldfred on 2018-05-14
Is this an Acer?

Acer have an unique requirement of setting an UEFI password with Secure Boot on and then enabling "trust" on the Ubuntu/grub .efi boot file in the ESP from within UEFI.
Also many have to update UEFI from Acer.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by tororii on 2018-05-14
Yes it is. Thanks!

---

